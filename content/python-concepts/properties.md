---
title: Properties
date: 2026-03-28
author: Your Name
cell_count: 1
score: 0
---

```python
class Temperature:
    def __init__(self, celsius):
        # We use an underscore to indicate this is an internal variable
        self._celsius = celsius

    @property
    def celsius(self):
        """The getter method."""
        return self._celsius

    @celsius.setter
    def celsius(self, value):
        """The setter method, allowing for validation."""
        if value < -273.15:
            raise ValueError("Temperature cannot go below absolute zero.")
        self._celsius = value

    @property
    def fahrenheit(self):
        """A derived property that computes its value on the fly."""
        return (self._celsius * 9/5) + 32

# Using the class
temp = Temperature(25)
print(f"Celsius: {temp.celsius}") # Accessing like an attribute, not a method
print(f"Fahrenheit: {temp.fahrenheit}")

# Attempting to set an invalid temperature will raise the ValueError
# temp.celsius = -300
```


---
**Score: 0**