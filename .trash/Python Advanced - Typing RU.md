# Python Advanced — Typing (RU)

> EN: [[Python Advanced - Typing]]

---

### В1: Type hints enforced at runtime?

**Типичный ответ:**  
Нет (по умолчанию). Для mypy/pyright/IDE/docs. Runtime-валидация — отдельно (Pydantic и т.п.).

**Источник:** [PEP 484](https://peps.python.org/pep-0484/)

---

### В2: `list[int]` vs `List[int]`?

**Типичный ответ:**  
С 3.9 (PEP 585) предпочитаем built-in generics. `typing.List` — legacy.

**Источник:** [PEP 585](https://peps.python.org/pep-0585/)

---

### В3: Generics / TypeVar?

**Типичный ответ:**  
Параметризация типов; связь input/output. 3.12+ синтаксис PEP 695: `def f[T](...):`.

**Источник:** [PEP 695](https://peps.python.org/pep-0695/)

---

### В4: Protocol vs ABC vs inheritance?

**Типичный ответ:**  
Protocol — structural; ABC — nominal/abstract; inheritance — shared implementation.

**Источник:** [PEP 544](https://peps.python.org/pep-0544/)

---

### В5: TypedDict / NamedTuple / dataclass?

**Типичный ответ:**  
TypedDict — форма dict (JSON). NamedTuple — immutable record. Dataclass — boilerplate для structured data.

**Источник:** [PEP 589](https://peps.python.org/pep-0589/) · [`dataclasses`](https://docs.python.org/3/library/dataclasses.html)

---

### В6: `Optional[T]` vs `T | None`?

**Типичный ответ:**  
Эквивалентны; с 3.10 предпочтительнее `T | None` (PEP 604).

**Источник:** [PEP 604](https://peps.python.org/pep-0604/)

---

### В7: ParamSpec?

**Типичный ответ:**  
Точная типизация декораторов, пробрасывающих `*args/**kwargs`.

**Источник:** [PEP 612](https://peps.python.org/pep-0612/)

---

### В8: Literal / Final / ClassVar?

**Типичный ответ:**  
Literal — точные значения; Final — не переназначать; ClassVar — поле класса, не instance (важно для dataclass).

**Источник:** [`typing`](https://docs.python.org/3/library/typing.html)

---

### В9: Gradual typing в команде?

**Типичный ответ:**  
С публичных API; strictness наращивать; Protocol на границах; runtime validation на untrusted input.

**Источник:** [`typing`](https://docs.python.org/3/library/typing.html)

---

## Связанное

- [[Advanced Python Interview Index RU]]
