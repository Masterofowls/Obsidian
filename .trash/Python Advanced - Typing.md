# Python Advanced — Typing

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: Are type hints enforced at runtime?

**Common answer:**  
No (by default). Annotations are for tools (mypy, pyright), IDEs, and documentation. At runtime you can read them via `__annotations__` / `typing.get_type_hints`, and libraries may validate (Pydantic), but CPython does not type-check execution.

**Reference:**  
[PEP 484 – Type Hints](https://peps.python.org/pep-0484/) · [`typing` module](https://docs.python.org/3/library/typing.html)

---

### Q2: `list[int]` vs `typing.List[int]`?

**Common answer:**  
Since 3.9 (PEP 585), built-in generics like `list[int]`, `dict[str, int]` are preferred. `typing.List` remains for older versions. In 3.7+ with `from __future__ import annotations`, annotations can be postponed (strings) for forward refs / less runtime cost.

**Reference:**  
[PEP 585 – Type Hinting Generics In Standard Collections](https://peps.python.org/pep-0585/) · [PEP 563 / PEP 649 annotation evolution](https://peps.python.org/pep-0649/)

---

### Q3: What are generics and `TypeVar`?

**Common answer:**  
Generics parameterize types (`class Stack[T]: ...`). `TypeVar` names type variables for functions/classes so input/output types relate. Use bounds/constraints for limited polymorphism. Python 3.12+ introduces cleaner syntax via PEP 695 (`def f[T](...):`).

**Reference:**  
[PEP 484 – Generics](https://peps.python.org/pep-0484/) · [PEP 695 – Type Parameter Syntax](https://peps.python.org/pep-0695/)

---

### Q4: `Protocol` vs ABC vs inheritance?

**Common answer:**  
`Protocol` = structural subtyping for static checkers (duck typing). ABC = nominal abstract base, often with runtime enforcement. Concrete inheritance shares implementation. Choose based on whether you need runtime `isinstance`, shared code, or just typechecker contracts.

**Reference:**  
[PEP 544 – Protocols](https://peps.python.org/pep-0544/)

---

### Q5: `TypedDict`, `NamedTuple`, dataclasses — when?

**Common answer:**  
- **TypedDict**: typed `dict` shapes (JSON APIs) without turning into objects.  
- **NamedTuple**: immutable lightweight records.  
- **dataclass**: generated `__init__`/`__repr__`/etc.; mutable by default; great for structured data.  
- **Pydantic** (third-party): runtime validation.

**Reference:**  
[PEP 589 – TypedDict](https://peps.python.org/pep-0589/) · [`dataclasses`](https://docs.python.org/3/library/dataclasses.html) · [`typing.NamedTuple`](https://docs.python.org/3/library/typing.html#typing.NamedTuple)

---

### Q6: `Optional[T]` vs `T | None`?

**Common answer:**  
Same idea: value may be `T` or `None`. Prefer `T | None` (3.10+, PEP 604). `Optional[T]` is historical sugar for `Union[T, None]`.

**Reference:**  
[PEP 604 – Allow writing union types as `X | Y`](https://peps.python.org/pep-0604/)

---

### Q7: What is `ParamSpec` / `Concatenate` for?

**Common answer:**  
They type decorators and higher-order functions that forward `*args/**kwargs` accurately—preserving the wrapped callable’s parameter types in the wrapper’s signature for type checkers.

**Reference:**  
[PEP 612 – Parameter Specification Variables](https://peps.python.org/pep-0612/)

---

### Q8: `Literal`, `Final`, `ClassVar`?

**Common answer:**  
- **Literal**: exact values (e.g. modes `"r"|"w"`).  
- **Final**: name should not be reassigned / method not overridden (checker-enforced).  
- **ClassVar**: class-level attribute, not instance field (important for dataclasses).

**Reference:**  
[`typing.Literal`](https://docs.python.org/3/library/typing.html#typing.Literal) · [`typing.Final`](https://docs.python.org/3/library/typing.html#typing.Final) · [`typing.ClassVar`](https://docs.python.org/3/library/typing.html#typing.ClassVar)

---

### Q9: Gradual typing strategy in a real codebase?

**Common answer:**  
Start with public APIs and critical modules; enable strictness incrementally; use `Protocol` at boundaries; keep runtime validation where untrusted data enters; don’t “type paint” internal noise. Tools: mypy/pyright + CI.

**Reference:**  
[typing — module docs](https://docs.python.org/3/library/typing.html) · [mypy docs (tooling)](https://mypy.readthedocs.io/)

---

## Related

- [[Python Advanced - Metaclasses And ABC]]
- [[Python Advanced - Data Model And Dunders]]
- [[Advanced Python Interview Index]]
