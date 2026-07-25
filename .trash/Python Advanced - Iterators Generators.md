# Python Advanced — Iterators And Generators

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: Iterator vs iterable?

**Common answer:**  
- **Iterable**: implements `__iter__` returning an iterator (or sequence-like `__getitem__`).  
- **Iterator**: implements `__next__` and `__iter__` (returns self).  
`iter(x)` gets an iterator; `next(it)` pulls values until `StopIteration`.

**Reference:**  
[Glossary — iterable / iterator](https://docs.python.org/3/glossary.html#term-iterable) · [Iterator types](https://docs.python.org/3/library/stdtypes.html#iterator-types)

---

### Q2: What is a generator?

**Common answer:**  
A generator is a function with `yield` (or a generator expression). Calling it returns a generator iterator that produces values lazily, suspending state between yields. Generators are memory-efficient for large or infinite streams.

**Reference:**  
[Yield expressions](https://docs.python.org/3/reference/expressions.html#yieldexpr) · [Generators](https://docs.python.org/3/glossary.html#term-generator)

---

### Q3: What does `yield from` do?

**Common answer:**  
`yield from subgen` delegates to a sub-iterator/generator: yields all its values, propagates `.send`/`.throw`, and returns the subgenerator’s return value. Cleaner than manual loops over nested generators.

**Reference:**  
[PEP 380 – Syntax for Delegating to a Subgenerator](https://peps.python.org/pep-0380/) · [yield from](https://docs.python.org/3/reference/expressions.html#yieldexpr)

---

### Q4: Generator `.send()`, `.throw()`, `.close()`?

**Common answer:**  
Generators are coroutines in the classic sense: `.send(value)` resumes and injects a value as the result of the current `yield`. `.throw` injects exceptions; `.close` raises `GeneratorExit` for cleanup. Modern `async`/`await` is the preferred structured model for concurrent I/O.

**Reference:**  
[Generator-iterator methods](https://docs.python.org/3/reference/expressions.html#generator-iterator-methods)

---

### Q5: Generator expression vs list comprehension?

**Common answer:**  
`[x for x in xs]` builds a full list eagerly. `(x for x in xs)` is lazy—good for pipelines and large data. Note: a generator expression can be consumed only once.

**Reference:**  
[Displays for lists, sets and dictionaries](https://docs.python.org/3/reference/expressions.html#displays-for-lists-sets-and-dictionaries) · [Generator expressions](https://docs.python.org/3/reference/expressions.html#generator-expressions)

---

### Q6: How does `for` loop work internally?

**Common answer:**  
Roughly: `it = iter(obj)` then repeatedly `next(it)` until `StopIteration`. The loop binds each value and exits cleanly on stop. Custom iterables implement this protocol.

**Reference:**  
[The for statement](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement)

---

### Q7: `itertools` — what should a senior know?

**Common answer:**  
`itertools` provides fast, memory-efficient building blocks: `chain`, `islice`, `groupby`, `product`, `combinations`, `cycle`, `tee`, etc. Prefer composing iterators over materializing large intermediate lists.

**Reference:**  
[`itertools`](https://docs.python.org/3/library/itertools.html)

---

### Q8: Exhaustion and reusability?

**Common answer:**  
Iterators/generators are typically **single-pass**. Lists/tuples are multi-pass iterables (each `iter()` makes a new iterator). If you need to reuse, materialize (`list(gen)`) or recreate the generator.

**Reference:**  
[Iterator types](https://docs.python.org/3/library/stdtypes.html#iterator-types)

---

### Q9: Async iterators / `async for`?

**Common answer:**  
Objects with `__aiter__` / `__anext__` support `async for`. Async generators use `async def` + `yield`. Used for streaming APIs, websockets, and paginated async I/O.

**Reference:**  
[PEP 525 – Asynchronous Generators](https://peps.python.org/pep-0525/) · [Async iterator](https://docs.python.org/3/reference/datamodel.html#asynchronous-iterators)

---

## Related

- [[Python Advanced - Asyncio]]
- [[Python Advanced - Data Model And Dunders]]
- [[Advanced Python Interview Index]]
