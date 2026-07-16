---
aliases: [python-functions, def-function, function-basics]
tags: [python, functions, def, parameters]
cssclass: reference
---
# Python Functions

## Defining Functions

```python
def greet(name):
    return f"Hello, {name}!"

def greet(name="World"):
    return f"Hello, {name}!"
```

## Parameters

```python
# Default
def greet(name="World"):

# Keyword
def greet(*, name, age):

# Arbitrary
def func(*args):
def func(**kwargs):

# Type hints
def greet(name: str) -> str:
```

## Lambda

```python
square = lambda x: x ** 2
add = lambda a, b: a + b
```

## Related

- [[Python\OOP|OOP]]
