# Python Advanced — Data Model And Dunders

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is the Python data model?

**Common answer:**  
The data model is the set of rules and special methods (`__…__`, “dunders”) that define how objects interact with the language: attribute access, operators, iteration, context managers, hashing, equality, and more. Writing correct dunders makes your types behave like built-ins.

**Reference:**  
[Python Language Reference — Data model](https://docs.python.org/3/reference/datamodel.html)

---

### Q2: What is the difference between `__repr__` and `__str__`?

**Common answer:**  
`__repr__` is the unambiguous developer-facing representation (ideally `eval`-able or clear for debugging). `__str__` is the readable, user-facing string. `print(x)` and `str(x)` use `__str__` (falling back to `__repr__`). Containers call `__repr__` on their elements.

**Reference:**  
[Data model — `object.__repr__` / `object.__str__`](https://docs.python.org/3/reference/datamodel.html#object.__repr__)

---

### Q3: How do equality and hashing work together?

**Common answer:**  
If two objects compare equal (`__eq__`), they must have the same hash (`__hash__`) when hashable. Mutable objects that define value equality usually set `__hash__ = None` so they cannot be dict keys/set members. Immutable value types implement both consistently.

**Reference:**  
[Data model — `__hash__`](https://docs.python.org/3/reference/datamodel.html#object.__hash__) · [Glossary — hashable](https://docs.python.org/3/glossary.html#term-hashable)

---

### Q4: What is the difference between `__new__` and `__init__`?

**Common answer:**  
`__new__` is a static-like constructor that creates and returns the instance (used for immutables, singletons, subclassing built-ins). `__init__` initializes an already-created instance and must return `None`. For normal classes you override `__init__`; override `__new__` when you need to control *creation*.

**Reference:**  
[Data model — `__new__`](https://docs.python.org/3/reference/datamodel.html#object.__new__)

---

### Q5: Explain `__getitem__`, `__len__`, and the sequence protocol.

**Common answer:**  
Implementing `__getitem__` (and often `__len__`) lets an object support indexing/slicing and iteration. If `__iter__` is missing, Python can fall back to iterating indices `0..n-1` via `__getitem__` until `IndexError`. True sequences also support `len()` and usually define `__contains__` for efficiency.

**Reference:**  
[Data model — emulating container types](https://docs.python.org/3/reference/datamodel.html#emulating-container-types) · [Collections ABCs](https://docs.python.org/3/library/collections.abc.html)

---

### Q6: What are `__call__` and callable objects?

**Common answer:**  
Any object with `__call__` can be invoked like a function. This is how class instances act as function-like objects (e.g. stateful callables, decorators as classes). `callable(x)` is true for functions, methods, classes, and instances with `__call__`.

**Reference:**  
[Data model — `__call__`](https://docs.python.org/3/reference/datamodel.html#object.__call__) · [`callable()`](https://docs.python.org/3/library/functions.html#callable)

---

### Q7: How do operator overloads and reflected ops work (`__add__` vs `__radd__`)?

**Common answer:**  
Binary operators try the left operand’s method first (`a.__add__(b)`). If that returns `NotImplemented`, Python tries the reflected method on the right (`b.__radd__(a)`). This enables interoperability when the right-hand type “knows” how to combine with the left.

**Reference:**  
[Data model — emulating numeric types](https://docs.python.org/3/reference/datamodel.html#emulating-numeric-types)

---

### Q8: What does `__bool__` / truthiness mean?

**Common answer:**  
Boolean context uses `__bool__` if defined; otherwise `__len__` (zero is false). If neither exists, the object is true by default. Prefer explicit `__bool__` when “empty” is not about length.

**Reference:**  
[Data model — `__bool__`](https://docs.python.org/3/reference/datamodel.html#object.__bool__)

---

## Related

- [[Python Advanced - Descriptors And Properties]]
- [[Python Advanced - Metaclasses And ABC]]
- [[Advanced Python Interview Index]]
