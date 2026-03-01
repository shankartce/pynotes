---
title: Generators
date: 2026-03-02
author: Your Name
cell_count: 1
score: 0
---

```python
def fibonacci_generator(limit):
    """Generates Fibonacci numbers up to a specified limit."""
    a, b = 0, 1
    count = 0
    while count < limit:
        yield a
        a, b = b, a + b
        count += 1

# Iterating through the generator
# This uses very little memory, even if the limit was 1,000,000
for number in fibonacci_generator(7):
    print(number) 
# Output: 0, 1, 1, 2, 3, 5, 8
```


---
**Score: 0**