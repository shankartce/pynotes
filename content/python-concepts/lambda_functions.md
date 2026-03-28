---
title: Lambda Functions
date: 2026-03-28
author: Your Name
cell_count: 1
score: 0
---

```python
numbers = [1, 2, 3, 4, 5, 6]

# Use lambda with filter to keep even numbers
evens = list(filter(lambda n: n % 2 == 0, numbers))

# Use lambda with map to square each even number
squared_evens = list(map(lambda n: n ** 2, evens))

print("Even numbers:", evens)
print("Squared evens:", squared_evens)
```


---
**Score: 0**