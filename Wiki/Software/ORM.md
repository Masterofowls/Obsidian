---
aliases: [orm, object-relational-mapping, database-orm]
tags: [software, orm, database, mapping]
cssclass: wiki
---
# How ORM Works

## Overview
ORM (Object-Relational Mapping) maps **database tables** to **programming language objects**, allowing you to work with databases using code instead of raw SQL.

## How It Works
1. Define **models** that map to database tables
2. ORM generates SQL queries from your code
3. Results are returned as objects, not raw rows

## Example (Python SQLAlchemy)
```python
class User(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    age = Column(Integer)

# Query
users = session.query(User).filter(User.age > 25).all()
```

## Benefits
- Write code in your language, not SQL
- Prevents SQL injection (parameterized queries)
- Works with multiple databases without changing code
- Automatic type mapping

## Drawbacks
- Can be slower than optimized raw SQL
- Complex queries may be harder to express
- Adds abstraction overhead

## Related
- [[Wiki\Software\SQL|SQL]]
- [[Wiki\Security\SQL Injection|SQL Injection]]
