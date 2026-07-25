# Python Advanced — Closures, Decorators, Scopes

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What is the LEGB rule?

**Common answer:**  
Name lookup order: **L**ocal → **E**nclosing (non-local closures) → **G**lobal (module) → **B**uilt-in. `global` binds a name to the module scope; `nonlocal` binds to the nearest enclosing function scope (not global).

**Reference:**  
[Python Tutorial — Scopes and Namespaces](https://docs.python.org/3/tutorial/classes.html#python-scopes-and-namespaces) · [`global` / `nonlocal` statements](https://docs.python.org/3/reference/simple_stmts.html#the-global-statement)

---

### Q2: What is a closure?

**Common answer:**  
A closure is a function that remembers values from its enclosing scopes via cell variables, even after the outer function returns. Visible as `__closure__` on the function object. Classic use: factories, decorators, callbacks with configuration.

**Reference:**  
[Execution model — Naming and binding](https://docs.python.org/3/reference/executionmodel.html#naming-and-binding)

---

### Q3: Late-binding closure classic bug?

**Common answer:**  
```python
funcs = [lambda: i for i in range(3)]
# all return 2 — they close over the variable i, not its value at creation
```
Fix: default-arg binding `lambda i=i: i` or `functools.partial`.

**Reference:**  
[FAQ — Why do lambdas defined in a loop with different values all return the same result?](https://docs.python.org/3/faq/programming.html#why-do-lambdas-defined-in-a-loop-with-different-values-all-return-the-same-result)

---

### Q4: What is a decorator?

**Common answer:**  
A decorator is callable that takes a function/class and returns a replacement (usually a wrapper). `@dec` on `def f` is syntactic sugar for `f = dec(f)`. Decorators implement cross-cutting concerns: logging, timing, retries, auth, registration.

**Reference:**  
[Compound statements — Function definitions (decorators)](https://docs.python.org/3/reference/compound_stmts.html#function) · [`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### Q5: Why use `functools.wraps`?

**Common answer:**  
Wrappers hide the original `__name__`, `__doc__`, and signature unless you copy metadata. `@wraps(func)` updates the wrapper to look like the wrapped function—critical for debugging, OpenAPI, and tests.

**Reference:**  
[`functools.wraps`](https://docs.python.org/3/library/functools.html#functools.wraps)

---

### Q6: Decorator with arguments — how?

**Common answer:**  
Use a decorator factory: outer function receives decorator args, returns the real decorator, which returns the wrapper. Pattern: `@retry(times=3)` → `retry(times=3)(func)`.

**Reference:**  
[Primer on decorators (glossary / compound stmts)](https://docs.python.org/3/glossary.html#term-decorator)

---

### Q7: Class as decorator vs function as decorator?

**Common answer:**  
A class decorator uses `__init__(self, func)` + `__call__` for stateful wrapping. Function decorators are lighter. For classes-as-targets, decorators receive the class object after the body executes.

**Reference:**  
[Data model — `__call__`](https://docs.python.org/3/reference/datamodel.html#object.__call__)

---

### Q8: `staticmethod`, `classmethod`, `property` — differences?

**Common answer:**  
- **instance method**: receives `self`.  
- **classmethod**: receives `cls`; alternative constructors, polymorphic factories.  
- **staticmethod**: no automatic first arg; namespaced function on the class.  
- **property**: managed attribute via descriptor.

**Reference:**  
[`classmethod`](https://docs.python.org/3/library/functions.html#classmethod) · [`staticmethod`](https://docs.python.org/3/library/functions.html#staticmethod) · [`property`](https://docs.python.org/3/library/functions.html#property)

---

### Q9: What does `functools.lru_cache` do?

**Common answer:**  
Memoizes function results for hashable arguments with an LRU eviction policy. Great for pure expensive functions. Avoid on methods without care (`self` is part of the key) and on functions with unhashable args or side effects.

**Reference:**  
[`functools.lru_cache`](https://docs.python.org/3/library/functools.html#functools.lru_cache) · [`functools.cache`](https://docs.python.org/3/library/functools.html#functools.cache)

---

## Related

- [[Python Advanced - Descriptors And Properties]]
- [[Python Advanced - Iterators Generators]]
- [[Advanced Python Interview Index]]
