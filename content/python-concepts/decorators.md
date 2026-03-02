---
title: Decorators
date: 2026-03-03
author: Your Name
cell_count: 1
score: 0
---

```python
import time

def timer_decorator(func):
    """A decorator that prints the execution time of the function."""
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Function '{func.__name__}' executed in {end_time - start_time:.4f} seconds")
        return result
    return wrapper

@timer_decorator
def process_data():
    # Simulating a time-consuming task
    time.sleep(1.2)
    return "Data processing complete."

# Calling the decorated function
print(process_data())
```


---
**Score: 0**