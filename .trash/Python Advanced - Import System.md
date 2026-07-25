# Python Advanced — Import System

> Interview format: **Question** → **Common answer** → **Reference**

---

### Q1: What happens when you `import module`?

**Common answer:**  
Python checks `sys.modules` cache; on miss, finders on `sys.meta_path` locate a loader, execute the module’s code in its namespace, bind the module object, and cache it. Subsequent imports return the cached module.

**Reference:**  
[The import system](https://docs.python.org/3/reference/import.html) · [`sys.modules`](https://docs.python.org/3/library/sys.html#sys.modules)

---

### Q2: Absolute vs relative imports?

**Common answer:**  
Absolute: `import pkg.sub`. Relative: `from . import sibling`, `from .. import parent_level`—only inside packages. Prefer absolute imports for clarity in large apps; relative can be clean within packages.

**Reference:**  
[PEP 328 – Imports: Multi-Line and Absolute/Relative](https://peps.python.org/pep-0328/) · [Intra-package references](https://docs.python.org/3/reference/import.html#package-relative-imports)

---

### Q3: What is a package vs a module?

**Common answer:**  
A **module** is a loadable unit (usually a `.py` file). A **package** is a module with a `__path__` attribute (traditionally a directory with `__init__.py`; namespace packages can omit it). Packages contain submodules.

**Reference:**  
[Glossary — package / module](https://docs.python.org/3/glossary.html#term-package) · [Regular packages](https://docs.python.org/3/reference/import.html#regular-packages)

---

### Q4: Namespace packages (PEP 420)?

**Common answer:**  
Packages without `__init__.py` that can span multiple directories on `sys.path`. Useful for large distributed namespaces. Be careful with accidental folders that become importable.

**Reference:**  
[PEP 420 – Implicit Namespace Packages](https://peps.python.org/pep-0420/)

---

### Q5: `sys.path` vs editable installs / packaging?

**Common answer:**  
`sys.path` is the module search path (script dir, `PYTHONPATH`, site-packages, …). Proper packaging (`pyproject.toml`, pip install -e) is preferred over hacking `sys.path` in production code.

**Reference:**  
[`sys.path`](https://docs.python.org/3/library/sys.html#sys.path) · [Packaging user guide](https://packaging.python.org/)

---

### Q6: Circular imports — how to fix?

**Common answer:**  
Symptoms: partially initialized module attributes. Fixes: restructure dependencies, move imports inside functions, use interface modules, invert dependencies, or lazy imports. Design to avoid deep cycles.

**Reference:**  
[Import system — circular imports discussion in FAQ](https://docs.python.org/3/faq/programming.html#what-are-the-best-practices-for-using-import-in-a-module)

---

### Q7: `importlib` and dynamic imports?

**Common answer:**  
`importlib.import_module("a.b")` loads by string; useful for plugins. Loaders/finders can be customized for exotic sources. Prefer explicit registries over magic import side effects when possible.

**Reference:**  
[`importlib`](https://docs.python.org/3/library/importlib.html)

---

### Q8: What is `__all__`?

**Common answer:**  
Optional list defining public names for `from module import *`. Also documents the public API; does not strictly enforce privacy (`_private` is convention).

**Reference:**  
[Import system — `__all__`](https://docs.python.org/3/tutorial/modules.html#importing-from-a-package)

---

### Q9: Module reloading?

**Common answer:**  
`importlib.reload(module)` re-executes a module in-place. Fragile with existing references/objects; fine for REPL experiments, rare in production services (prefer process restart).

**Reference:**  
[`importlib.reload`](https://docs.python.org/3/library/importlib.html#importlib.reload)

---

## Related

- [[Python Advanced - Performance And Internals]]
- [[Advanced Python Interview Index]]
