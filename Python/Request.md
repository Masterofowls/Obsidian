---
aliases: [python-requests, http-requests, requests-module]
tags: [python, requests, http, api]
cssclass: reference
---
# Python Requests

## requests Library

```python
import requests

# GET
response = requests.get(url)
data = response.json()

# POST
response = requests.post(url, json=payload)

# With headers
headers = {'Authorization': 'Bearer token'}
response = requests.get(url, headers=headers)
```

## Related

- [[Python\Async|Async]]
