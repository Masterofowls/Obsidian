# Python Advanced — Memory And Garbage Collection

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: How does CPython manage memory?

**Common answer:**  
Primarily **reference counting**: each object tracks how many references point to it; at zero it is deallocated immediately. A **cyclic garbage collector** additionally finds and collects reference cycles that refcounting alone cannot free. Allocators (pymalloc, system malloc) sit underneath.

**Reference:**  
[`gc` module](https://docs.python.org/3/library/gc.html) · [C API — Memory Management](https://docs.python.org/3/c-api/memory.html)

---

### Q2: Why do we need a cyclic GC if we have refcounting?

**Common answer:**  
Cycles (e.g. `a.b = b; b.a = a`) keep refcounts above zero even when unreachable from the program. The cyclic GC identifies unreachable cycles among container objects and breaks/collects them. Non-cyclic garbage is usually freed instantly via refcount.

**Reference:**  
[gc — Garbage Collector interface](https://docs.python.org/3/library/gc.html)

---

### Q3: What are GC generations?

**Common answer:**  
CPython’s cyclic GC uses three generations. Newly created tracked objects start in generation 0; survivors are promoted. Younger generations are collected more often (generational hypothesis: most objects die young). Thresholds are tunable via `gc.set_threshold`.

**Reference:**  
[`gc.get_threshold` / generations](https://docs.python.org/3/library/gc.html#gc.get_threshold)

---

### Q4: What is a weak reference?

**Common answer:**  
A `weakref` references an object **without** increasing its refcount, so it doesn’t prevent collection. Useful for caches, observer patterns, and canonical maps (`WeakKeyDictionary`, `WeakValueDictionary`). When the object dies, the weakref becomes dead / callbacks fire.

**Reference:**  
[`weakref`](https://docs.python.org/3/library/weakref.html)

---

### Q5: `__del__` and finalizers — pitfalls?

**Common answer:**  
`__del__` is called when an object is about to be destroyed, but timing is not guaranteed (especially with cycles, interpreters shutting down, or alternate implementations). Prefer context managers / explicit close. Finalizers can resurrect objects or create cycles; they make GC harder.

**Reference:**  
[Data model — `__del__`](https://docs.python.org/3/reference/datamodel.html#object.__del__) · [gc — finalizers](https://docs.python.org/3/library/gc.html)

---

### Q6: How do you debug memory growth?

**Common answer:**  
Tools/approaches: `tracemalloc` (stdlib allocation traces), `gc.get_objects()`, `objgraph` (third-party), heapy/memray, process RSS monitoring, and checking for unbounded caches, global lists, or unclosed resources. First ask: leak vs high water mark vs fragmentation.

**Reference:**  
[`tracemalloc`](https://docs.python.org/3/library/tracemalloc.html) · [`gc`](https://docs.python.org/3/library/gc.html)

---

### Q7: Interning and small object caching?

**Common answer:**  
CPython interns some strings and caches small integers (implementation detail, historically -5..256). Identity (`is`) is not the same as equality (`==`). Never rely on `is` for integers/strings except known singletons (`None`, `True`, `False`).

**Reference:**  
[Integer objects — free list / small ints (C API notes vary by version)](https://docs.python.org/3/c-api/long.html) · [PEP 8 — comparisons](https://peps.python.org/pep-0008/#programming-recommendations)

---

### Q8: How does the GIL relate to memory management?

**Common answer:**  
The classic GIL design makes refcount increments/decrements safer without per-object atomics on every operation. Free-threaded builds change that model (more careful atomic refcounting / biased schemes). In interviews: “GIL simplified refcounting; free-threading reworks those assumptions.”

**Reference:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock) · [PEP 703](https://peps.python.org/pep-0703/)

---

## Related

- [[Python Advanced - GIL Concurrency Multiprocessing]]
- [[Python Advanced - Performance And Internals]]
- [[Advanced Python Interview Index]]
