---
title: Arguments
date: 2026-03-03
author: Your Name
cell_count: 1
score: 0
---

```python
def user_profile(name, *args, **kwargs):
    """Creates a user profile using unpacked arguments."""
    print(f"User: {name}")
    
    # *args is treated as a tuple of positional arguments
    if args:
        print("Additional skills:", ", ".join(args))
        
    # **kwargs is treated as a dictionary of keyword arguments
    if kwargs:
        for key, value in kwargs.items():
            print(f"{key.capitalize()}: {value}")

# Calling the function with a mix of arguments
user_profile(
    "Alice", 
    "Python", "SQL", "Machine Learning", # These become *args
    location="Madurai", role="Data Engineer", active=True # These become **kwargs
)
```


---
**Score: 0**