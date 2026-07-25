# Python Advanced — Практический опыт (собеседование)

> Формат: **Вопрос** → **Типичный ответ** → **Источник**  
> Для раунда «расскажите о проекте / почему / как». Подставляйте **свои** реальные примеры.

**English version:** [[Python Advanced - Practical Experience]]

---

### В1: Что такое декоратор и когда мы его используем?

**Типичный ответ:**  
Декоратор — вызываемый объект, который оборачивает функцию или класс, добавляя поведение без изменения основной логики. Синтаксис `@decorator` — сахар для `f = decorator(f)`. Используем для сквозных задач: логирование, замер времени, ретраи, проверка прав, кэш, метрики, валидация, регистрация обработчиков. Уместны, когда одна и та же обёртка нужна во многих местах; не уместны, если прячут важный control flow или без `functools.wraps` ломают отладку.

**Источник:**  
[Glossary — decorator](https://docs.python.org/3/glossary.html#term-decorator) · [`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### В2: Приведите реальный пример декоратора с работы.

**Типичный ответ:**  
Например `@retry(times=3, exceptions=(TimeoutError, ConnectionError))` на HTTP-клиенте; `@require_role("admin")` на API; `@timed` с метриками Prometheus. Реализация: фабрика при параметрах, учёт `async`, всегда `@wraps(func)`.

**Источник:**  
[`functools`](https://docs.python.org/3/library/functools.html) · [tenacity](https://github.com/jd/tenacity)

---

### В3: Как работает декоратор с аргументами?

**Типичный ответ:**  
`@retry(3)` значит: сначала вызывается `retry(3)`, он возвращает настоящий декоратор, затем применяется к функции. Три уровня: снаружи конфиг → принимает `func` → wrapper на каждый вызов.

**Источник:**  
[Function definitions](https://docs.python.org/3/reference/compound_stmts.html#function)

---

### В4: Когда декоратор *не* стоит использовать?

**Типичный ответ:**  
Когда логика разовая; когда проще явный вызов / middleware / DI; когда и так сложно дебажить. Чрезмерные декораторы превращают код в «магию».

**Источник:**  
[PEP 20 — Zen of Python](https://peps.python.org/pep-0020/)

---

### В5: Использовали ли вы асинхронность в проекте? Зачем?

**Типичный ответ:**  
*(Шаблон — заполните своим проектом.)* Да, когда узкое место — **ожидание** (HTTP, websocket, БД, брокеры), а не чистый CPU. Async позволил держать много одновременных I/O при меньшем числе потоков и памяти. Не использовали async как основной способ ускорить CPU-bound вычисления.

**Источник:**  
[`asyncio`](https://docs.python.org/3/library/asyncio.html)

---

### В6: Как именно была устроена асинхронность? (архитектура)

**Типичный ответ:**  
Типичный стек: event loop `asyncio` + фреймворк (FastAPI/Starlette/aiohttp), async-драйвер БД (asyncpg / SQLAlchemy async), HTTP-клиент (`httpx.AsyncClient` / `aiohttp`), structured concurrency (`TaskGroup` / `gather`), таймауты на внешние вызовы, CPU через `asyncio.to_thread` или process pool. Точка входа: ASGI (uvicorn).

**Источник:**  
[Coroutines and Tasks](https://docs.python.org/3/library/asyncio-task.html) · [PEP 492](https://peps.python.org/pep-0492/)

---

### В7: Async vs многопоточность — как выбирали?

**Типичный ответ:**  
I/O fan-out (много внешних сервисов) → async. Синхронный SDK → `to_thread` / executor или отдельный воркер. Тяжёлый CPU (картинки/видео) → очередь и процессы, не event loop API. Общее mutable-состояние → сообщения, а не locks «везде».

**Источник:**  
[`asyncio.to_thread`](https://docs.python.org/3/library/asyncio-task.html#asyncio.to_thread) · [`concurrent.futures`](https://docs.python.org/3/library/concurrent.futures.html)

---

### В8: Какие проблемы ловили с asyncio?

**Типичный ответ:**  
Блокирующий код в корутинах (кладёт весь loop); забытый `await`; Task без ссылок / «exception was never retrieved»; отмена без cleanup; sync ORM в async-ручке; исчерпание пула соединений; сложные тесты. Лечится: линтеры, таймауты, TaskGroup, async-драйверы, нагрузочные тесты.

**Источник:**  
[Developing with asyncio](https://docs.python.org/3/library/asyncio-dev.html)

---

### В9: Как отменяете работу и освобождаете ресурсы в async?

**Типичный ответ:**  
Таймауты (`asyncio.timeout` / `wait_for`), cancel при необходимости, `try/finally` или `async with` для сессий/соединений. В 3.11+ `TaskGroup` отменяет соседей при ошибке. Не глотать `CancelledError` бездумно.

**Источник:**  
[Task cancellation](https://docs.python.org/3/library/asyncio-task.html#task-cancellation) · [`TaskGroup`](https://docs.python.org/3/library/asyncio-task.html#task-groups)

---

### В10: Как тестировали асинхронный код?

**Типичный ответ:**  
`pytest-asyncio` / anyio, моки HTTP (respx), тесты cancel/timeout, unit без сети, integration с testcontainers для БД, проверка что не остаются pending tasks.

**Источник:**  
[`IsolatedAsyncioTestCase`](https://docs.python.org/3/library/unittest.html#unittest.IsolatedAsyncioTestCase) · [pytest-asyncio](https://pytest-asyncio.readthedocs.io/)

---

### В11: Использовали multiprocessing? Когда?

**Типичный ответ:**  
Да для CPU-bound батчей (парсинг, пре/постпроцесс ML, ресайз) и обхода GIL. Паттерн: `ProcessPoolExecutor` или воркеры очереди. Осторожно с `spawn` на Windows, pickle и `if __name__ == "__main__"`.

**Источник:**  
[`multiprocessing`](https://docs.python.org/3/library/multiprocessing.html) · [[Python Advanced - GIL Concurrency Multiprocessing]]

---

### В12: Как GIL повлиял на реальное решение?

**Типичный ответ:**  
Пример: параллель pure-Python трансформации JSON потоками не ускорила → process pool или нативное расширение. Потоки оставили для конкурентных загрузок (I/O отпускает GIL).

**Источник:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock)

---

### В13: Как делали retries и backoff?

**Типичный ответ:**  
Ретраим только идемпотентные/безопасные операции; exponential backoff + jitter; лимит попыток; 4xx обычно не ретраим (кроме 429 + Retry-After). В async — `asyncio.sleep`, не `time.sleep`.

**Источник:**  
[RFC 9110 — HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110.html)

---

### В14: Кэширование — что и зачем?

**Типичный ответ:**  
В процессе: `lru_cache` / `cache` для чистых функций. Между инстансами: Redis + TTL, cache-aside, инвалидация на записи. Не кэшировать чувствительные данные без изоляции ключей. Смотреть hit rate.

**Источник:**  
[`functools.lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache)

---

### В15: Как искали bottleneck по производительности?

**Типичный ответ:**  
Нагрузка → профиль (`cProfile`, pyinstrument) → правим топ (N+1 SQL, chatty HTTP, лишняя сериализация) → сравнение p95/CPU/`tracemalloc` до и после.

**Источник:**  
[Profilers](https://docs.python.org/3/library/profile.html) · [`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html)

---

### В16: Что такое N+1 и как чинили?

**Типичный ответ:**  
Список сущностей + запрос на каждый элемент в цикле. Фикс: join/eager load, batch `IN (...)`, DataLoader, read-model. Ловим логами SQL / APM.

**Источник:**  
[SQLAlchemy relationship loading](https://docs.sqlalchemy.org/en/20/orm/queryguide/relationships.html)

---

### В17: Async-доступ к БД — как делали?

**Типичный ответ:**  
Async engine, сессия на запрос, размер пула под воркеры, не шарить сессию между task, явные транзакции, statement timeout. Sync-сессию ORM в async-роуте без thread pool не держим.

**Источник:**  
[PEP 249](https://peps.python.org/pep-0249/) · SQLAlchemy asyncio

---

### В18: Какие context manager реально использовали?

**Типичный ответ:**  
Файлы, транзакции БД, Redis lock, HTTP-клиенты, temp dir, span трейсинга. В тестах — `@contextmanager` «выставить/вернуть» окружение.

**Источник:**  
[PEP 343](https://peps.python.org/pep-0343/) · [`contextlib`](https://docs.python.org/3/library/contextlib.html)

---

### В19: Генераторы в проде — пример?

**Типичный ответ:**  
Стриминг больших CSV/S3 построчно, постраничный обход API, ETL без загрузки всего в RAM. Async-генераторы для websocket.

**Источник:**  
[Generators](https://docs.python.org/3/glossary.html#term-generator) · [[Python Advanced - Iterators Generators]]

---

### В20: Как структурируете пакет/сервис?

**Типичный ответ:**  
Слои: `api` → `services` → `repositories` → `domain`. Конфиг из env (`pydantic-settings`), DI клиентов при старте, без циклических импортов. `src/`, `pyproject.toml`, ruff/mypy/pytest в CI.

**Источник:**  
[Packaging projects](https://packaging.python.org/en/latest/tutorials/packaging-projects/) · [PEP 621](https://peps.python.org/pep-0621/)

---

### В21: Dependency injection в Python?

**Типичный ответ:**  
Constructor injection (db/http в сервис), а не глобальные синглтоны. FastAPI `Depends` или composition root в `main`. Скрытый global state мешает тестам.

**Источник:**  
[FastAPI Depends](https://fastapi.tiangolo.com/tutorial/dependencies/)

---

### В22: Конфигурация и секреты?

**Типичный ответ:**  
12-factor: env / secret manager, секреты не в git, разные env, типизированные settings, fail-fast при старте если нет обязательных переменных.

**Источник:**  
[12-Factor — Config](https://12factor.net/config)

---

### В23: Логирование vs print?

**Типичный ответ:**  
Structured logging (`logging` + JSON), request/correlation id, уровни, без секретов в логах, централизованный сбор. `print` — только локально.

**Источник:**  
[`logging`](https://docs.python.org/3/library/logging.html)

---

### В24: Стратегия обработки исключений?

**Типичный ответ:**  
Ловим конкретные типы на границах; маппим в domain/HTTP ошибки; не `except:`; логируем unexpected со стеком; иерархия своих исключений; `ExceptionGroup` при нескольких сбоях task.

**Источник:**  
[Errors tutorial](https://docs.python.org/3/tutorial/errors.html) · [PEP 654](https://peps.python.org/pep-0654/)

---

### В25: Как защищаете Python web API?

**Типичный ответ:**  
AuthN/AuthZ, валидация входа, параметризованный SQL, rate limit, TLS, least-privilege к БД, обновления зависимостей, безопасная десериализация (не pickle от недоверенных).

**Источник:**  
[OWASP API Security](https://owasp.org/www-project-api-security/) · [pickle](https://docs.python.org/3/library/pickle.html)

---

### В26: Почему `pickle` опасен для недоверенных данных?

**Типичный ответ:**  
При load может выполниться произвольный код. Для внешних данных — JSON/msgpack/protobuf. Pickle — только доверенный внутренний контур (и то с осторожностью).

**Источник:**  
[`pickle` security](https://docs.python.org/3/library/pickle.html)

---

### В27: Type hints в команде — как?

**Типичный ответ:**  
На публичных API и моделях; CI mypy/pyright; Protocol на границах; gradual typing для legacy; runtime-валидация (Pydantic) на входе API.

**Источник:**  
[PEP 484](https://peps.python.org/pep-0484/) · [[Python Advanced - Typing]]

---

### В28: Рефакторинг legacy Python?

**Типичный ответ:**  
Сначала characterization-тесты, маленькие шаги, strangler, типы на краях, дробим god-modules, покрытие. Не big-bang rewrite без страховки.

**Источник:**  
[Working Effectively with Legacy Code (concept)](https://en.wikipedia.org/wiki/Working_Effectively_with_Legacy_Code)

---

### В29: Очереди (Celery и т.п.) vs asyncio?

**Типичный ответ:**  
Очередь: фоновые job, ретраи, cron, масштаб на много машин, изоляция от latency API. Asyncio: конкурентный I/O внутри процесса/запроса. Часто вместе: async API + Celery/RQ/Arq для тяжёлого/отложенного.

**Источник:**  
[Celery](https://docs.celeryq.dev/) · [`asyncio`](https://docs.python.org/3/library/asyncio.html)

---

### В30: Rate limiting — как?

**Типичный ответ:**  
Token bucket / sliding window в Redis или на gateway. 429 + Retry-After. Лимиты per-user / per-IP. Сначала дорогие эндпоинты.

**Источник:**  
[RFC 6585 — 429](https://www.rfc-editor.org/rfc/rfc6585)

---

### В31: Миграции БД — подход?

**Типичный ответ:**  
Expand/contract: сначала additive миграция, код совместим со старым и новым, потом удаление старого. Бэкфиллы джобами. Деструктивное — только с бэкапом и планом. Alembic/Django migrations в review CI.

**Источник:**  
[Alembic](https://alembic.sqlalchemy.org/)

---

### В32: Утечка памяти — как дебажить?

**Типичный ответ:**  
Рост RSS → `tracemalloc` / objgraph → безграничные кэши, global list, незакрытые сокеты, listeners, растущие пулы. Фикс: TTL, weakref, close, лимиты пулов.

**Источник:**  
[`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html) · [`gc`](https://docs.python.org/3/library/gc.html)

---

### В33: Race / deadlock, который чинили?

**Типичный ответ:**  
*(Шаблон истории.)* Race: check-then-act без синхронизации → `asyncio.Lock` или atomic Redis SET NX. Deadlock: два lock в разном порядке → единый порядок захвата или одна блокировка / очередь сообщений.

**Источник:**  
[`threading.Lock`](https://docs.python.org/3/library/threading.html#lock-objects) · [`asyncio.Lock`](https://docs.python.org/3/library/asyncio-sync.html)

---

### В34: Metaclass / descriptors на проекте?

**Типичный ответ:**  
Metaclass редко (лучше `__init_subclass__` / декораторы). Property/descriptors — да (валидация, lazy, ORM-поля в библиотеках). Если metaclass — для declarative registry, с обоснованием почему проще не вышло.

**Источник:**  
[Descriptor HowTo](https://docs.python.org/3/howto/descriptor.html) · [PEP 487](https://peps.python.org/pep-0487/)

---

### В35: Плагины / registry?

**Типичный ответ:**  
`@register_handler("event")`, entry points (`importlib.metadata`), `__init_subclass__`. Явное discovery предпочтительнее скрытой магии на import.

**Источник:**  
[entry points](https://docs.python.org/3/library/importlib.metadata.html#entry-points)

---

### В36: Версии Python и зависимости?

**Типичный ответ:**  
Пиним Python в CI/Docker, lock-файлы (uv/poetry/pip-tools), воспроизводимые образы, те же версии что в prod, план апгрейда 3.x→3.y.

**Источник:**  
[Status of Python versions](https://devguide.python.org/versions/) · [pip](https://pip.pypa.io/)

---

### В37: Docker для Python — грабли?

**Типичный ответ:**  
Multi-stage, non-root, секреты не в слоях, `.dockerignore`, gunicorn/uvicorn workers, healthcheck, не слепой `latest`, кэш слоёв: deps до кода.

**Источник:**  
[Multi-stage builds](https://docs.docker.com/build/building/multi-stage/)

---

### В38: Observability — что отдавали?

**Типичный ответ:**  
Метрики RED/USE, structured logs, трейсы (OpenTelemetry), health/readiness, бизнес-метрики. SLO на p95 и error rate.

**Источник:**  
[OpenTelemetry Python](https://opentelemetry.io/docs/languages/python/)

---

### В39: Идемпотентные API?

**Типичный ответ:**  
Idempotency-Key на POST, upsert/natural key, таблица дедупа, consumer at-least-once безопасен к повтору. Критично для платежей и webhook.

**Источник:**  
[RFC 9110 — idempotent methods](https://www.rfc-editor.org/rfc/rfc9110.html#name-idempotent-methods)

---

### В40: Стриминг больших ответов/файлов?

**Типичный ответ:**  
Генераторы / streaming ASGI response; не читать файл целиком в память; chunked; upload стримом в object storage.

**Источник:**  
[ASGI](https://asgi.readthedocs.io/en/latest/) · generators

---

### В41: Feature flags?

**Типичный ответ:**  
Флаги в конфиге/Redis, ветвление в service layer, default safe off, удалять старые флаги, тесты обоих путей.

**Источник:**  
Индустриальная практика (LaunchDarkly-style)

---

### В42: Monkey patching — когда и риски?

**Типичный ответ:**  
В тестах (`mock.patch`) или hotfix. Риски: порядок, скрытое поведение, поломка при апдейте. Архитектурно — DI и обёртки, не patch.

**Источник:**  
[`unittest.mock`](https://docs.python.org/3/library/unittest.mock.html)

---

### В43: Как ревьюите Python PR?

**Типичный ответ:**  
Корректность, edge cases, blocking в async, SQL safety, тесты, типы, сложность, observability, rollback. Маленькие PR. CI — обязательный gate.

**Источник:**  
[PEP 8](https://peps.python.org/pep-0008/)

---

### В44: Инцидент в проде с Python (STAR).

**Типичный ответ:**  
**S:** рост latency. **T:** вернуть p95. **A:** нашли pool exhaustion + sync в async-роуте; async-драйвер, timeout, лимиты пула; тест + дашборд. **R:** p95 в SLO, повторов нет.

**Источник:**  
[asyncio debug](https://docs.python.org/3/library/asyncio-dev.html)

---

### В45: Почему Python для этого сервиса (и когда нет)?

**Типичный ответ:**  
Плюсы: скорость разработки, экосистема, найм, читаемость. Минусы: CPU scale (процессы/native), дисциплина packaging, GIL. Не лучший одиночный выбор для ultra-low-latency HFT без native; отлично для API, оркестрации, data-сервисов.

**Источник:**  
[python.org success stories](https://www.python.org/about/success/)

---

## Банк коротких историй (проговорить вслух)

| Промпт | Вопросы |
|--------|---------|
| Декоратор, который писали | В1–В4 |
| Async в проекте | В5–В10 |
| GIL / CPU | В11–В12 |
| Perf / SQL | В15–В17 |
| Надёжность | В13, В30, В39 |
| Инцидент | В44 |

## Связанные заметки

- [[Advanced Python Interview Index RU]]
- [[Advanced Python Interview Index]]
- [[Python Advanced - Practical Experience]]
- [[Python Advanced - Closures Decorators Scopes]]
- [[Python Advanced - Asyncio]]
