---
title: Exception Handling
date: 2026-03-28
author: Your Name
cell_count: 1
score: 0
---

```python
def safe_divide(a, b):
    try:
        result = a / b
    except ZeroDivisionError:
        return "Cannot divide by zero."
    except TypeError:
        return "Inputs must be numbers."
    else:
        return f"Result: {result}"

print(safe_divide(10, 2))
print(safe_divide(10, 0))
print(safe_divide(10, "x"))
```


---
**Score: 0**