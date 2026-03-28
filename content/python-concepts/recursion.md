---
title: Recursion
date: 2026-03-28
author: Your Name
cell_count: 1
score: 0
---

```python
def factorial(n):
    if n < 0:
        raise ValueError("n must be a non-negative integer")
    if n in (0, 1):
        return 1
    return n * factorial(n - 1)

for value in range(6):
    print(f"factorial({value}) = {factorial(value)}")
```


---
**Score: 0**