# Python Advanced — Metaclasses And ABC

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is a metaclass?

**Common answer:**  
A metaclass is the class of a class. Just as instances are created from classes, classes are created from metaclasses (default `type`). Metaclasses customize class creation: registration, interface enforcement, API rewriting. Prefer simpler tools (`__init_subclass__`, decorators) unless you need deep control.

**Reference:**  
[Data model — Metaclasses](https://docs.python.org/3/reference/datamodel.html#metaclasses) · [Customizing class creation](https://docs.python.org/3/reference/datamodel.html#customizing-class-creation)

---

### Q2: What happens when you define a class body?

**Common answer:**  
Python executes the class body in a namespace dict, then calls `Metaclass(name, bases, namespace, **kw)` to build the class object. Hooks: metaclass `__prepare__`, `__new__`, `__init__`; also `__set_name__` on descriptors and `__init_subclass__` on bases.

**Reference:**  
[PEP 3115 – Metaclasses in Python 3000](https://peps.python.org/pep-3115/) · [PEP 487](https://peps.python.org/pep-0487/)

---

### Q3: `type` as a metaclass — examples?

**Common answer:**  
`type(name, bases, dict)` dynamically builds classes. `type(obj)` returns an instance’s class; `type(cls)` returns the metaclass. Most “magic” frameworks use metaclasses or `__init_subclass__` for declarative APIs (ORMs, serializers).

**Reference:**  
[`type`](https://docs.python.org/3/library/functions.html#type)

---

### Q4: When would you use `__init_subclass__` instead of a metaclass?

**Common answer:**  
For inheritance hooks on subclasses (registration, validation) without the complexity of metaclasses. It’s the modern default for many plugin patterns.

**Reference:**  
[PEP 487 – `__init_subclass__`](https://peps.python.org/pep-0487/) · [`__init_subclass__`](https://docs.python.org/3/reference/datamodel.html#object.__init_subclass__)

---

### Q5: What are ABCs?

**Common answer:**  
Abstract Base Classes (`abc` module) define abstract methods/properties that subclasses must implement. They support `isinstance`/`issubclass` checks and virtual subclassing via `register()`. Useful for formal interfaces without full inheritance trees.

**Reference:**  
[`abc` — Abstract Base Classes](https://docs.python.org/3/library/abc.html)

---

### Q6: `@abstractmethod` behavior?

**Common answer:**  
Decorating methods as abstract prevents instantiation of the class until all abstract methods are overridden. Works with `@property`, `@classmethod`, etc., when composed correctly.

**Reference:**  
[`abc.abstractmethod`](https://docs.python.org/3/library/abc.html#abc.abstractmethod)

---

### Q7: Structural typing vs ABCs (`Protocol`)?

**Common answer:**  
ABCs are often **nominal** (inheritance or register). `typing.Protocol` enables **structural** (“has these methods”) typing for static checkers, with optional runtime checks via `@runtime_checkable`. Prefer protocols for duck typing + type checkers; ABCs when you need shared implementation or classic registry.

**Reference:**  
[PEP 544 – Protocols](https://peps.python.org/pep-0544/) · [`typing.Protocol`](https://docs.python.org/3/library/typing.html#typing.Protocol)

---

### Q8: `collections.abc` — why interviewers care?

**Common answer:**  
It defines standard interfaces (`Iterable`, `Sequence`, `Mapping`, `Awaitable`, …). Implementing the right dunders and registering/subclassing makes your types play with `isinstance` and static reasoning. Also documents which methods are required for each concept.

**Reference:**  
[`collections.abc`](https://docs.python.org/3/library/collections.abc.html)

---

### Q9: Metaclass pitfalls?

**Common answer:**  
Multiple inheritance with conflicting metaclasses (`TypeError: metaclass conflict`), overuse where a decorator would do, harder debugging, and surprise behavior in libraries. Rule of thumb: if you can solve it with `__init_subclass__` or a class decorator, do that.

**Reference:**  
[Data model — Metaclasses](https://docs.python.org/3/reference/datamodel.html#metaclasses)

---

## Related

- [[Python Advanced - Data Model And Dunders]]
- [[Python Advanced - Typing]]
- [[Advanced Python Interview Index]]
