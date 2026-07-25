# Python Advanced — Practical Experience Interview

> Format: **Question** → **Common answer** → **Reference**  
> Use these for “tell me about a project / why / how” rounds. Adapt examples to **your** real work.

**Russian version:** [[Python Advanced - Practical Experience RU]]

---

### Q1: What is a decorator, and when do we use it?

**Common answer:**  
A decorator is a callable that wraps a function or class to add behavior without changing its core logic. Syntax `@decorator` is sugar for `f = decorator(f)`. We use it for cross-cutting concerns: logging, timing, retries, auth/permission checks, caching, metrics, validating inputs, registering handlers. Prefer decorators when the same wrapping appears in many places; avoid them when they hide critical control flow or make stack traces hard to read without `functools.wraps`.

**Reference:**  
[Glossary — decorator](https://docs.python.org/3/glossary.html#term-decorator) · [`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### Q2: Give a real example of a decorator you would write at work.

**Common answer:**  
Example: `@retry(times=3, exceptions=(TimeoutError, ConnectionError))` on HTTP client methods; or `@require_role("admin")` on API handlers; or `@timed` that emits Prometheus metrics. Implementation: factory if parameters are needed, wrap with `async` awareness if the target is a coroutine, always `@wraps(func)`.

**Reference:**  
[`functools`](https://docs.python.org/3/library/functools.html) · [tenacity (common retry lib, third-party)](https://github.com/jd/tenacity)

---

### Q3: Decorator with arguments — how does it work?

**Common answer:**  
`@retry(3)` means “call `retry(3)` first; that returns the real decorator; then apply it to the function.” Three nested levels: outer (config) → middle (receives `func`) → inner (wrapper that runs on each call).

**Reference:**  
[Compound statements — Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function)

---

### Q4: When would you *not* use a decorator?

**Common answer:**  
When logic is one-off, when you need different behavior per call site that isn’t config, when debugging is already hard, or when a simple function call / middleware / dependency injection is clearer. Over-decorating turns code into “magic.”

**Reference:**  
[PEP 20 — Zen of Python (explicit is better)](https://peps.python.org/pep-0020/)

---

### Q5: Did you use asynchronous code in a project? Why?

**Common answer:**  
*(Template — fill with your project.)* Yes, when the bottleneck was **waiting** (HTTP APIs, websockets, DB, message brokers), not pure CPU. Async let us handle many concurrent I/O operations with fewer threads and lower memory than one-thread-per-connection. We did **not** use async primarily to speed up CPU-bound number crunching.

**Reference:**  
[`asyncio`](https://docs.python.org/3/library/asyncio.html)

---

### Q6: How was async done in the project? (architecture)

**Common answer:**  
Typical stack: `asyncio` event loop + framework (FastAPI/Starlette/aiohttp), async DB driver (asyncpg / SQLAlchemy async), HTTP client (`httpx.AsyncClient` / `aiohttp`), structured concurrency with `TaskGroup` or `gather`, timeouts on every external call, and CPU work offloaded via `asyncio.to_thread` or a process pool. Entry: `uvicorn`/ASGI workers.

**Reference:**  
[Coroutines and Tasks](https://docs.python.org/3/library/asyncio-task.html) · [PEP 492](https://peps.python.org/pep-0492/)

---

### Q7: Async vs multi-threading in *your* service — how did you choose?

**Common answer:**  
I/O-heavy fan-out (call 20 services) → async. Blocking third-party SDK that is sync-only → threads via `to_thread`/`run_in_executor`, or isolate in a worker process. CPU-heavy image/video → separate worker processes / queue, not the API event loop. Shared mutable state → prefer messages over threads+locks.

**Reference:**  
[`asyncio.to_thread`](https://docs.python.org/3/library/asyncio-task.html#asyncio.to_thread) · [`concurrent.futures`](https://docs.python.org/3/library/concurrent.futures.html)

---

### Q8: What problems did you hit with asyncio?

**Common answer:**  
Common real issues: accidentally calling blocking code (freezes all requests); forgotten `await`; tasks created without references / exception logging; cancellation not cleaning resources; mixing sync ORM in async views; connection pool exhaustion; testing complexity. Fix: lint for blocking calls, timeouts, TaskGroup, async-native drivers, load tests.

**Reference:**  
[Developing with asyncio](https://docs.python.org/3/library/asyncio-dev.html)

---

### Q9: How do you cancel work and clean up in async?

**Common answer:**  
Use timeouts (`asyncio.timeout` / `wait_for`), cancel tasks on client disconnect if applicable, always `try/finally` or `async with` for sessions/connections. In 3.11+, `TaskGroup` cancels siblings on failure. Don’t swallow `CancelledError`.

**Reference:**  
[Task cancellation](https://docs.python.org/3/library/asyncio-task.html#task-cancellation) · [`asyncio.TaskGroup`](https://docs.python.org/3/library/asyncio-task.html#task-groups)

---

### Q10: How did you test asynchronous code?

**Common answer:**  
`pytest-asyncio` (or anyio), fixture for event loop, mock external I/O with respx/aioresponses, test cancellation and timeouts, avoid real network in unit tests, integration tests against testcontainers for DB. Assert task cleanup (no pending tasks warnings).

**Reference:**  
[`unittest.IsolatedAsyncioTestCase`](https://docs.python.org/3/library/unittest.html#unittest.IsolatedAsyncioTestCase) · [pytest-asyncio](https://pytest-asyncio.readthedocs.io/)

---

### Q11: Have you used multiprocessing? When?

**Common answer:**  
Yes for CPU-bound batch jobs (parsing, ML pre/post-process, image resize) and to bypass the GIL. Pattern: `ProcessPoolExecutor` or a job queue worker. Careful with Windows `spawn`, pickling, and `if __name__ == "__main__"`.

**Reference:**  
[`multiprocessing`](https://docs.python.org/3/library/multiprocessing.html) · [[Python Advanced - GIL Concurrency Multiprocessing]]

---

### Q12: How did the GIL affect a real decision?

**Common answer:**  
Example: parallelizing pure-Python JSON transform with threads gave no speedup → switched to process pool or a Rust/Cython extension. Threads still used for concurrent downloads because I/O releases the GIL.

**Reference:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock)

---

### Q13: How do you implement retries and backoff?

**Common answer:**  
Retry only **idempotent** or safely retriable ops; exponential backoff + jitter; cap attempts; don’t retry 4xx (except 429 with Retry-After). Library: tenacity or custom decorator. For async, sleep with `asyncio.sleep`, not `time.sleep`.

**Reference:**  
[HTTP Semantics — retry considerations (RFC 9110)](https://www.rfc-editor.org/rfc/rfc9110.html)

---

### Q14: Caching — what did you use and why?

**Common answer:**  
In-process: `functools.lru_cache` / `cache` for pure functions. Multi-instance: Redis with TTL, cache-aside pattern, explicit invalidation on writes. Never cache unauthenticated sensitive data without key isolation. Measure hit rate.

**Reference:**  
[`functools.lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache)

---

### Q15: How did you find a performance bottleneck?

**Common answer:**  
Reproduce with load → profile (`cProfile`, pyinstrument, continuous profiling) → fix the top hotspots (SQL N+1, chatty HTTP, unnecessary serialization). Confirm with before/after metrics (p95 latency, CPU, allocations via `tracemalloc`).

**Reference:**  
[Profilers](https://docs.python.org/3/library/profile.html) · [`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html)

---

### Q16: N+1 queries — what is it and how did you fix it?

**Common answer:**  
Loading a list then querying per item in a loop. Fixes: `select_related`/`joinedload` (ORM), batch `WHERE id IN (...)`, DataLoader pattern, denormalized read models. Detect with query logging or APM.

**Reference:**  
[SQLAlchemy relationship loading](https://docs.sqlalchemy.org/en/20/orm/queryguide/relationships.html) (if ORM) · general DB design

---

### Q17: Async DB access — how was it done?

**Common answer:**  
Async engine + session per request, pool size tuned to workers, no sharing sessions across tasks, transactions with explicit commit/rollback, timeouts on statements. Avoid running sync SQLAlchemy session inside async routes without a thread pool.

**Reference:**  
[PEP 249 DB-API (sync baseline)](https://peps.python.org/pep-0249/) · SQLAlchemy asyncio docs

---

### Q18: Context managers you actually used?

**Common answer:**  
File I/O, DB transactions, Redis locks, `httpx` clients, temp directories, feature-flag scopes, tracing spans. Custom `@contextmanager` for “set env / restore” in tests.

**Reference:**  
[PEP 343](https://peps.python.org/pep-0343/) · [`contextlib`](https://docs.python.org/3/library/contextlib.html)

---

### Q19: Generators in production — example?

**Common answer:**  
Streaming large CSV/S3 files line-by-line, paging API results (`yield from` pages), ETL pipelines without loading entire datasets into RAM. Async generators for websocket fan-in.

**Reference:**  
[Generators](https://docs.python.org/3/glossary.html#term-generator) · [[Python Advanced - Iterators Generators]]

---

### Q20: How do you structure a Python package/service?

**Common answer:**  
Layers: `api` (HTTP) → `services` (use-cases) → `repositories` (DB) → `domain` models. Config via env (`pydantic-settings`), DI of clients at startup, no circular imports. `src/` layout, `pyproject.toml`, ruff/mypy/pytest in CI.

**Reference:**  
[Packaging Python Projects](https://packaging.python.org/en/latest/tutorials/packaging-projects/) · [PEP 518/621 pyproject](https://peps.python.org/pep-0621/)

---

### Q21: Dependency injection in Python?

**Common answer:**  
Prefer constructor injection (pass db/session/http client into services) over global singletons. FastAPI `Depends`, or manual composition root in `main`. Avoid hidden imports of global state for testability.

**Reference:**  
[FastAPI Depends (framework pattern)](https://fastapi.tiangolo.com/tutorial/dependencies/) · general composition

---

### Q22: Configuration and secrets?

**Common answer:**  
12-factor: env vars / secret manager, never commit secrets, separate config per environment, typed settings objects, fail fast on missing required config at startup.

**Reference:**  
[12-Factor App — Config](https://12factor.net/config)

---

### Q23: Logging vs print — production approach?

**Common answer:**  
Structured logging (`logging` + JSON formatter), correlation/request IDs, appropriate levels, no secrets in logs, central aggregation. `print` only for quick local debug.

**Reference:**  
[`logging`](https://docs.python.org/3/library/logging.html)

---

### Q24: Exception handling strategy?

**Common answer:**  
Catch specific exceptions at boundaries; translate to domain/HTTP errors; don’t bare `except:`; log with stack at unexpected failures; use custom exception hierarchy; `ExceptionGroup` when multiple tasks fail.

**Reference:**  
[Errors and Exceptions tutorial](https://docs.python.org/3/tutorial/errors.html) · [PEP 654](https://peps.python.org/pep-0654/)

---

### Q25: How do you secure a Python web API?

**Common answer:**  
AuthN/AuthZ (JWT/session/OAuth2), input validation, parameterized SQL, CSRF where applicable, rate limits, TLS, least-privilege DB users, dependency updates, safe deserialization (no pickle from untrusted sources).

**Reference:**  
[OWASP API Security](https://owasp.org/www-project-api-security/) · [pickle warning](https://docs.python.org/3/library/pickle.html)

---

### Q26: Why is `pickle` dangerous for untrusted data?

**Common answer:**  
Pickle can execute arbitrary code during load. Use JSON/msgpack/protobuf for untrusted inputs. Pickle only for trusted internal caches if at all.

**Reference:**  
[`pickle` — security considerations](https://docs.python.org/3/library/pickle.html)

---

### Q27: Type hints — did your team use them? How?

**Common answer:**  
Yes on public functions and domain models; CI with mypy/pyright in non-zero mode for touched packages; Protocols at boundaries; gradual typing for legacy. Runtime validation (Pydantic) at API edges.

**Reference:**  
[PEP 484](https://peps.python.org/pep-0484/) · [[Python Advanced - Typing]]

---

### Q28: Refactoring legacy Python — approach?

**Common answer:**  
Characterization tests first, small steps, strangler pattern, add types at edges, kill god-modules, extract pure functions, measure coverage. Don’t big-bang rewrite without a safety net.

**Reference:**  
[Working Effectively with Legacy Code (concept)](https://en.wikipedia.org/wiki/Working_Effectively_with_Legacy_Code)

---

### Q29: Celery / task queues vs asyncio?

**Common answer:**  
Queue workers: background jobs, retries, scheduling, multi-machine fan-out, isolation from API latency. Asyncio: concurrent I/O inside one process/request path. Often both: API async + Celery/RQ/Arq for heavy or delayed work.

**Reference:**  
[Celery docs](https://docs.celeryq.dev/) · [`asyncio`](https://docs.python.org/3/library/asyncio.html)

---

### Q30: Rate limiting — how?

**Common answer:**  
Token bucket / sliding window in Redis, or gateway (nginx/API gateway). Return 429 + Retry-After. Per-user and per-IP policies. Protect expensive endpoints first.

**Reference:**  
[RFC 6585 — 429 Too Many Requests](https://www.rfc-editor.org/rfc/rfc6585)

---

### Q31: How do you handle migrations?

**Common answer:**  
Expand/contract: additive migrations first, deploy code that works with old+new, then remove old columns. Backfills as jobs. Never destructive migration without backup and lock plan. Alembic/Django migrations in CI review.

**Reference:**  
[Alembic](https://alembic.sqlalchemy.org/) · expand-contract pattern (industry practice)

---

### Q32: Memory leak story — how would you debug?

**Common answer:**  
Confirm growth (RSS metrics) → `tracemalloc` snapshots / objgraph → look for caches without bound, global lists, unclosed sockets, listener refs, growing thread pools. Fix with TTLs, weakrefs, explicit close, pool limits.

**Reference:**  
[`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html) · [`gc`](https://docs.python.org/3/library/gc.html)

---

### Q33: Deadlock or race you fixed?

**Common answer:**  
*(Story template.)* Race: check-then-act on shared flag without lock → fixed with `asyncio.Lock` or atomic Redis SET NX. Deadlock: two locks acquired in opposite order → consistent lock ordering or single lock / message queue.

**Reference:**  
[`threading.Lock`](https://docs.python.org/3/library/threading.html#lock-objects) · [`asyncio.Lock`](https://docs.python.org/3/library/asyncio-sync.html)

---

### Q34: Have you used metaclasses or descriptors in a project?

**Common answer:**  
Rarely metaclasses (prefer `__init_subclass__` / decorators). Descriptors/properties yes: validated fields, lazy attributes, ORM-style columns (library code). If I wrote a metaclass, it was for a declarative plugin registry—and I’d justify why simpler options failed.

**Reference:**  
[Descriptor HowTo](https://docs.python.org/3/howto/descriptor.html) · [PEP 487](https://peps.python.org/pep-0487/)

---

### Q35: Plugin / registry architecture?

**Common answer:**  
Decorator-based registration (`@register_handler("event")`), entry points (`importlib.metadata`), or `__init_subclass__` auto-register. Explicit discovery beats import-time side-effect magic when possible.

**Reference:**  
[`importlib.metadata` entry points](https://docs.python.org/3/library/importlib.metadata.html#entry-points)

---

### Q36: How do you manage Python versions and deps?

**Common answer:**  
Pin Python in CI and Docker (e.g. 3.12), lock files (uv/poetry/pip-tools), reproducible images, test on the same version as prod, plan upgrades (3.x → 3.y) with deprecation cleanup.

**Reference:**  
[Status of Python versions](https://devguide.python.org/versions/) · [pip freeze / lock tooling](https://pip.pypa.io/)

---

### Q37: Dockerizing a Python app — pitfalls?

**Common answer:**  
Multi-stage builds, non-root user, no secrets in layers, `.dockerignore`, correct `WORKDIR`, gunicorn/uvicorn workers formula, healthchecks, don’t run `latest` blindly, compile bytecode optional, install deps before copying code for layer cache.

**Reference:**  
[Docker best practices (multi-stage)](https://docs.docker.com/build/building/multi-stage/)

---

### Q38: Observability — what did you emit?

**Common answer:**  
RED/USE metrics, structured logs, traces (OpenTelemetry), health/readiness probes, business metrics (orders_created). Profile continuous in staging. SLOs on p95 latency and error rate.

**Reference:**  
[OpenTelemetry Python](https://opentelemetry.io/docs/languages/python/)

---

### Q39: How do you design idempotent APIs?

**Common answer:**  
Idempotency keys for POSTs, natural keys/upserts, dedupe tables, at-least-once consumers that can re-run safely. Critical for payments and webhook handlers.

**Reference:**  
[HTTP idempotency (RFC 9110)](https://www.rfc-editor.org/rfc/rfc9110.html#name-idempotent-methods)

---

### Q40: Streaming responses / large downloads?

**Common answer:**  
Stream with generators / ASGI streaming responses; never `read()` whole file into memory; use chunked transfer; backpressure awareness; for uploads, stream to object storage.

**Reference:**  
[PEP 3333 WSGI / ASGI streaming concepts](https://asgi.readthedocs.io/en/latest/) · generators docs

---

### Q41: How do you handle feature flags?

**Common answer:**  
Flags in config service/Redis, short-circuit in service layer, default-safe off, cleanup old flags, don’t scatter magic booleans without ownership. Test both paths.

**Reference:**  
Industry practice (LaunchDarkly-style); keep logic explicit in Python services

---

### Q42: Monkey patching — ever used? Risks?

**Common answer:**  
Sometimes in tests (`unittest.mock.patch`) or emergency hotfixes. Risks: order dependence, hidden behavior, break on upgrades. Prefer DI and wrappers; never patch as primary architecture.

**Reference:**  
[`unittest.mock`](https://docs.python.org/3/library/unittest.mock.html)

---

### Q43: How do you review Python PRs?

**Common answer:**  
Correctness, edge cases, async/blocking mistakes, SQL safety, tests, types, complexity, observability, rollback plan. Prefer small PRs. Run linters/tests in CI as gate.

**Reference:**  
[PEP 8](https://peps.python.org/pep-0008/) · team engineering guidelines

---

### Q44: Tell me about a production incident involving Python.

**Common answer:**  
*(STAR template.)* **S**ituation: latency spike. **T**ask: restore p95. **A**ction: traced to pool exhaustion + sync call in async route; fixed by async driver + timeout + pool limits; added regression test and dashboard. **R**esult: p95 back under SLO, no recurrence.

**Reference:**  
Use your real metrics; methodology: [asyncio debug](https://docs.python.org/3/library/asyncio-dev.html)

---

### Q45: Why Python for this service (and when not)?

**Common answer:**  
Pros: speed of delivery, ecosystem (data/web/ML), hiring, readability. Cons: CPU-bound scale (need processes/native), packaging discipline, GIL caveats. Not ideal alone for ultra-low-latency HFT without native extensions; fine for APIs, orchestration, data services.

**Reference:**  
[Python.org success stories / general positioning](https://www.python.org/about/success/)

---

## Quick “story bank” prompts (practice aloud)

| Prompt | Map to |
|--------|--------|
| Decorator you wrote | Q1–Q4 |
| Async in project | Q5–Q10 |
| GIL / CPU | Q11–Q12 |
| Perf / SQL | Q15–Q17 |
| Reliability | Q13, Q30, Q39 |
| Incident | Q44 |

## Related

- [[Advanced Python Interview Index]]
- [[Python Advanced - Closures Decorators Scopes]]
- [[Python Advanced - Asyncio]]
- [[Python Advanced - GIL Concurrency Multiprocessing]]
- [[Python Advanced - Practical Experience RU]]
