# Python Advanced — Import System (RU)

> EN: [[Python Advanced - Import System]]

---

### В1: Что делает `import module`?

**Типичный ответ:**  
Проверка `sys.modules` → finders/loaders на `sys.meta_path` → exec модуля → cache.

**Источник:** [The import system](https://docs.python.org/3/reference/import.html)

---

### В2: Absolute vs relative imports?

**Типичный ответ:**  
Absolute: `import pkg.sub`. Relative: `from . import x` только внутри packages.

**Источник:** [PEP 328](https://peps.python.org/pep-0328/)

---

### В3: Package vs module?

**Типичный ответ:**  
Module — единица загрузки. Package — module с `__path__` (часто dir + `__init__.py`).

**Источник:** [Glossary — package](https://docs.python.org/3/glossary.html#term-package)

---

### В4: Namespace packages (PEP 420)?

**Типичный ответ:**  
Package без `__init__.py`, может spanning несколько директорий.

**Источник:** [PEP 420](https://peps.python.org/pep-0420/)

---

### В5: `sys.path` vs packaging?

**Типичный ответ:**  
Search path модулей. В проде — нормальный install/editable, не хак `sys.path`.

**Источник:** [`sys.path`](https://docs.python.org/3/library/sys.html#sys.path)

---

### В6: Circular imports?

**Типичный ответ:**  
Частично инициализированный module. Фикс: реструктуризация, local import, invert deps.

**Источник:** [Import FAQ](https://docs.python.org/3/faq/programming.html#what-are-the-best-practices-for-using-import-in-a-module)

---

### В7: `importlib` / dynamic import?

**Типичный ответ:**  
`import_module("a.b")` для плагинов. Лучше явные registries.

**Источник:** [`importlib`](https://docs.python.org/3/library/importlib.html)

---

### В8: `__all__`?

**Типичный ответ:**  
Публичные имена для `import *` и документация API. Не строгий privacy.

**Источник:** [Modules tutorial](https://docs.python.org/3/tutorial/modules.html#importing-from-a-package)

---

### В9: `reload`?

**Типичный ответ:**  
`importlib.reload` — хрупко; в сервисах чаще restart process.

**Источник:** [`reload`](https://docs.python.org/3/library/importlib.html#importlib.reload)

---

## Связанное

- [[Advanced Python Interview Index RU]]
