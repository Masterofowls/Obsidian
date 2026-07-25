# Python Advanced — Performance And Internals

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: How do you find performance bottlenecks in Python?

**Common answer:**  
Measure first: `cProfile`/`profile`, `pyinstrument`, `scalene`, `perf` (Linux), tracing. Optimize hotspots only. Common wins: algorithmic complexity, fewer allocations, vectorization (NumPy), caching, moving hot loops to Cython/Rust/C, concurrency model fit.

**Reference:**  
[The Python Profilers](https://docs.python.org/3/library/profile.html) · [Performance tips (wiki, supplementary)](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)

---

### Q2: What is bytecode / `dis`?

**Common answer:**  
CPython compiles source to bytecode executed by the evaluation loop (ceval). `dis.dis(f)` disassembles functions—useful to understand comprehensions, load/store ops, and some performance nuances. Not portable across implementations.

**Reference:**  
[`dis` — Disassembler](https://docs.python.org/3/library/dis.html) · [Code objects](https://docs.python.org/3/reference/datamodel.html#code-objects)

---

### Q3: Why are list comprehensions often faster than manual loops?

**Common answer:**  
They push iteration into optimized C-level loops in CPython with fewer bytecode ops / less Python-level overhead for simple transforms. Still secondary to algorithmic complexity; readability matters.

**Reference:**  
[Functional Programming HOWTO](https://docs.python.org/3/howto/functional.html) · [Displays / comprehensions](https://docs.python.org/3/reference/expressions.html#displays-for-lists-sets-and-dictionaries)

---

### Q4: `dict` / hash table performance characteristics?

**Common answer:**  
Average O(1) lookup/insert for hashable keys; worst-case pathological hashing is mitigated by salted hashes. Memory overhead for sparse tables. Ordered by insertion (language guarantee since 3.7).

**Reference:**  
[Mapping types — dict](https://docs.python.org/3/library/stdtypes.html#mapping-types-dict) · [What’s New in Python 3.6 — New dict implementation](https://docs.python.org/3/whatsnew/3.6.html#new-dict-implementation) · [What’s New in 3.7 — ordered dict language guarantee](https://docs.python.org/3/whatsnew/3.7.html)

---

### Q5: String concatenation performance?

**Common answer:**  
Repeated `s += chunk` in a loop can be quadratic in older patterns; prefer `''.join(parts)`, `io.StringIO`, or bytearray for binary. CPython may optimize some cases, but `join` is the clear idiom.

**Reference:**  
[Common pitfalls — string concat (programming FAQ)](https://docs.python.org/3/faq/programming.html#what-is-the-most-efficient-way-to-concatenate-many-strings-together)

---

### Q6: When do you use `__slots__` for performance?

**Common answer:**  
Many small instances: reduced memory and slightly faster attribute access by avoiding per-instance `__dict__`. Measure; don’t use by default on all classes.

**Reference:**  
[Data model — `__slots__`](https://docs.python.org/3/reference/datamodel.html#slots)

---

### Q7: Specializing adaptive interpreter (3.11+)?

**Common answer:**  
CPython 3.11+ added specializing adaptive bytecode (PEP 659) and faster exception handling—often large speedups without code changes. Know that performance characteristics evolve by version.

**Reference:**  
[PEP 659 – Specializing Adaptive Interpreter](https://peps.python.org/pep-0659/) · [What’s New in Python 3.11](https://docs.python.org/3/whatsnew/3.11.html)

---

### Q8: Multithreading, multiprocessing, asyncio — pick for performance?

**Common answer:**  
- **I/O-bound, many connections**: asyncio or threads.  
- **CPU-bound pure Python**: processes / native extensions / free-threaded builds carefully.  
- **Shared-memory numerical**: often NumPy/SciPy releasing GIL.  
Always match tool to bottleneck type.

**Reference:**  
[[Python Advanced - GIL Concurrency Multiprocessing]] · [[Python Advanced - Asyncio]]

---

### Q9: Memory vs speed trade-offs seniors mention?

**Common answer:**  
Caches (`lru_cache`), preallocation, generators vs lists, `__slots__`, data layout (struct-of-arrays vs objects), and moving work to libraries. Explicit trade-off language impresses interviewers more than micro-benchmark trivia.

**Reference:**  
[`functools.lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache) · [`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html)

---

## Related

- [[Python Advanced - Memory And Garbage Collection]]
- [[Python Advanced - GIL Concurrency Multiprocessing]]
- [[Advanced Python Interview Index]]
