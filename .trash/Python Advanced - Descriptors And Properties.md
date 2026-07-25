# Python Advanced — Descriptors And Properties

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is a descriptor?

**Common answer:**  
A descriptor is an object that defines `__get__`, `__set__`, and/or `__delete__` and is stored on a class. Attribute access on instances is mediated by the descriptor protocol, which is how `property`, methods, `classmethod`, and `staticmethod` work under the hood.

**Reference:**  
[Descriptor HowTo Guide](https://docs.python.org/3/howto/descriptor.html) · [Data model — Implementing Descriptors](https://docs.python.org/3/reference/datamodel.html#implementing-descriptors)

---

### Q2: Data descriptor vs non-data descriptor?

**Common answer:**  
- **Data descriptor:** defines `__set__` and/or `__delete__` (e.g. `property`). Takes precedence over the instance `__dict__`.  
- **Non-data descriptor:** only `__get__` (e.g. functions/methods). Instance attributes override them if present on the instance.

**Reference:**  
[Descriptor HowTo — Descriptor protocol](https://docs.python.org/3/howto/descriptor.html#descriptor-protocol)

---

### Q3: How does `property` work?

**Common answer:**  
`property` is a data descriptor that routes attribute get/set/delete to user functions. `@x.setter` / `@x.deleter` attach managed accessors. Use it for computed attributes, validation, or lazy fields without changing the public attribute API.

**Reference:**  
[`property`](https://docs.python.org/3/library/functions.html#property)

---

### Q4: Why do methods become bound methods on instance access?

**Common answer:**  
Function objects on classes are non-data descriptors. Their `__get__` returns a bound method that injects `self`. Accessing the same function on the class returns the raw function (or unbound behavior depending on version/context).

**Reference:**  
[Descriptor HowTo — Methods and functions](https://docs.python.org/3/howto/descriptor.html#functions-and-methods)

---

### Q5: What is `__slots__` and when do you use it?

**Common answer:**  
`__slots__` declares a fixed set of instance attributes and typically **suppresses** per-instance `__dict__` (unless you include `'__dict__'`). Benefits: lower memory per instance and faster attribute access in some cases. Costs: less dynamic attributes, inheritance rules are tricky, weaker pickling unless handled.

**Reference:**  
[Data model — `__slots__`](https://docs.python.org/3/reference/datamodel.html#slots)

---

### Q6: Explain attribute lookup order (simplified).

**Common answer:**  
Roughly: data descriptors on the class → instance `__dict__` → non-data descriptors / class attributes → then `__getattr__` if defined. `__getattribute__` is the full machinery; override it carefully and call `object.__getattribute__` to avoid recursion.

**Reference:**  
[Data model — Customizing attribute access](https://docs.python.org/3/reference/datamodel.html#customizing-attribute-access)

---

### Q7: `__getattr__` vs `__getattribute__`?

**Common answer:**  
`__getattribute__` runs on **every** attribute access. `__getattr__` runs only when normal lookup fails (missing attribute). Prefer `__getattr__` for lazy/default attributes; use `__getattribute__` only when you must intercept all access.

**Reference:**  
[Data model — `__getattribute__` / `__getattr__`](https://docs.python.org/3/reference/datamodel.html#object.__getattribute__)

---

### Q8: What did PEP 487 change for descriptors / subclassing?

**Common answer:**  
PEP 487 introduced `__init_subclass__` and `__set_name__`. `__set_name__` lets a descriptor learn the attribute name it was assigned to on the owner class—important for reusable descriptors without explicit name passing.

**Reference:**  
[PEP 487 – Simpler customisation of class creation](https://peps.python.org/pep-0487/) · [`__set_name__`](https://docs.python.org/3/reference/datamodel.html#object.__set_name__)

---

## Related

- [[Python Advanced - Data Model And Dunders]]
- [[Python Advanced - Metaclasses And ABC]]
- [[Advanced Python Interview Index]]
