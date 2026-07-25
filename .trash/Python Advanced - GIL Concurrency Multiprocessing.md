# Python Advanced — GIL, Concurrency, Multiprocessing

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is the GIL?

**Common answer:**  
The Global Interpreter Lock is a mutex in CPython that allows only one thread to execute Python bytecode at a time in a process. It simplifies memory management (refcount) but limits CPU-bound multi-threading. I/O-bound threads can still make progress because the GIL is released around many blocking I/O operations.

**Reference:**  
[Glossary — global interpreter lock](https://docs.python.org/3/glossary.html#term-global-interpreter-lock) · [CPython design docs — GIL](https://docs.python.org/3/c-api/init.html#thread-state-and-the-global-interpreter-lock)

---

### Q2: Threads vs processes for concurrency in Python?

**Common answer:**  
- **`threading`**: good for I/O-bound work; shared memory; limited by GIL for pure-Python CPU work.  
- **`multiprocessing`**: separate interpreters/processes; true parallel CPU work; higher overhead; use queues/pipes/shared memory for IPC.  
- **`concurrent.futures`**: high-level `ThreadPoolExecutor` / `ProcessPoolExecutor` API over both.

**Reference:**  
[`threading`](https://docs.python.org/3/library/threading.html) · [`multiprocessing`](https://docs.python.org/3/library/multiprocessing.html) · [`concurrent.futures`](https://docs.python.org/3/library/concurrent.futures.html)

---

### Q3: Why doesn’t multi-threading speed up pure Python CPU loops?

**Common answer:**  
Because of the GIL, only one thread runs Python bytecode at a time. Threads still context-switch, so CPU-bound pure Python can be as slow or slower. Parallelism comes from processes, native extensions that release the GIL, or free-threaded builds (experimental).

**Reference:**  
[GIL glossary](https://docs.python.org/3/glossary.html#term-global-interpreter-lock)

---

### Q4: When is multi-threading still useful?

**Common answer:**  
I/O-bound workloads (network, disk), overlapping waits, UI responsiveness, and libraries that release the GIL in C (e.g. many NumPy ops). For high concurrency I/O, also consider `asyncio` instead of many threads.

**Reference:**  
[`threading` — intro](https://docs.python.org/3/library/threading.html) · [[Python Advanced - Asyncio]]

---

### Q5: What is free-threading / no-GIL Python?

**Common answer:**  
Starting with experimental support in recent CPython (e.g. 3.13 free-threaded builds), the GIL can be disabled so multiple threads run Python code truly in parallel. Trade-offs include performance differences for single-threaded code and ongoing ecosystem compatibility work. Treat as opt-in and version-dependent in interviews unless the company targets it.

**Reference:**  
[What’s New in Python 3.13 — Free-threaded CPython](https://docs.python.org/3/whatsnew/3.13.html#free-threaded-cpython) · [PEP 703 – Making the GIL Optional](https://peps.python.org/pep-0703/)

---

### Q6: What is a per-interpreter GIL?

**Common answer:**  
PEP 684 allows subinterpreters to each have their own GIL, so multiple interpreters in one process can run Python code in parallel (with isolation constraints). This is different from free-threading within one interpreter.

**Reference:**  
[PEP 684 – A Per-Interpreter GIL](https://peps.python.org/pep-0684/) · [What’s New in 3.12](https://docs.python.org/3/whatsnew/3.12.html)

---

### Q7: How do you share state safely across threads?

**Common answer:**  
Use locks (`threading.Lock`, `RLock`), condition variables, queues (`queue.Queue` is thread-safe), and avoid shared mutable state when possible. Prefer message-passing. Note: the GIL is **not** a substitute for correct synchronization of your application data structures.

**Reference:**  
[`threading` synchronization](https://docs.python.org/3/library/threading.html#lock-objects) · [`queue`](https://docs.python.org/3/library/queue.html)

---

### Q8: `multiprocessing` start methods — spawn vs fork?

**Common answer:**  
- **fork** (Unix default historically): child inherits parent memory via copy-on-write; unsafe with multithreaded parents.  
- **spawn** (default on Windows/macOS recent): fresh interpreter, re-import main; safer, slower startup.  
- **forkserver**: dedicated server process forks children.  
Always guard entry with `if __name__ == "__main__":` especially under spawn.

**Reference:**  
[multiprocessing — Contexts and start methods](https://docs.python.org/3/library/multiprocessing.html#contexts-and-start-methods)

---

### Q9: Race conditions and deadlocks — quick senior answer?

**Common answer:**  
A race is when result depends on scheduling of concurrent access without adequate sync. Deadlocks occur from circular lock acquisition. Mitigations: minimize shared state, consistent lock ordering, timeouts, higher-level concurrency primitives, and prefer immutable messages.

**Reference:**  
[`threading` — Lock](https://docs.python.org/3/library/threading.html#lock-objects)

---

## Related

- [[Python Advanced - Asyncio]]
- [[Python Advanced - Memory And Garbage Collection]]
- [[Advanced Python Interview Index]]
