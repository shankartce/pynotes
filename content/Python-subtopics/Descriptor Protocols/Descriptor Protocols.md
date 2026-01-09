---
title: Descriptor Protocols
date: 2026-01-09
author: Your Name
cell_count: 11
score: 10
---

```python
class Descriptor:
    def __get__(self, instance, owner):
        print("Getting value")
        return instance._value
    
    def __set__(self, instance, value):
        print("Setting value")
        instance._value = value

class MyClass:
    attribute = Descriptor()

obj = MyClass()
obj.attribute = 42  # Setting value
print(obj.attribute)  # Getting value, Output: 42
```

    Setting value
    Getting value
    42
    


```python
class ReadOnlyDescriptor:
    def __get__(self, instance, owner):
        return "This is a read-only attribute"

    def __set__(self, instance, value):
        raise AttributeError("Cannot modify read-only attribute")

class MyClass:
    read_only = ReadOnlyDescriptor()

obj = MyClass()
print(obj.read_only)  # Output: This is a read-only attribute
# obj.read_only = "New value"  # Raises AttributeError
```

    This is a read-only attribute
    


```python
class PositiveNumber:
    def __get__(self, instance, owner):
        return instance._number

    def __set__(self, instance, value):
        if value < 0:
            raise ValueError("Number must be positive")
        instance._number = value

class MyClass:
    number = PositiveNumber()

obj = MyClass()
obj.number = 10
print(obj.number)  # Output: 10
# obj.number = -5  # Raises ValueError
```

    10
    


```python
class NonDataDescriptor:
    def __get__(self, instance, owner):
        return "Non-data descriptor called"

class MyClass:
    attribute = NonDataDescriptor()

obj = MyClass()
print(obj.attribute)  # Output: Non-data descriptor called
```

    Non-data descriptor called
    


```python
class Descriptor:
    def __get__(self, instance, owner):
        return "Class-level descriptor"

class MyClass:
    attribute = Descriptor()

print(MyClass.attribute)  # Output: Class-level descriptor
```

    Class-level descriptor
    


```python
class Descriptor:
    def __get__(self, instance, owner):
        return instance.__dict__.get("_value", None)

    def __set__(self, instance, value):
        print(f"Setting value to {value}")
        instance.__dict__["_value"] = value

class MyClass:
    attribute = Descriptor()

obj = MyClass()
obj.attribute = "Hello"
print(obj.attribute)  # Output: Hello
```

    Setting value to Hello
    Hello
    


```python
class TrackingDescriptor:
    def __init__(self):
        self.access_count = 0

    def __get__(self, instance, owner):
        self.access_count += 1
        return f"Accessed {self.access_count} times"

class MyClass:
    tracked = TrackingDescriptor()

obj = MyClass()
print(obj.tracked)  # Output: Accessed 1 times
print(obj.tracked)  # Output: Accessed 2 times
```

    Accessed 1 times
    Accessed 2 times
    


```python
class ControlledAttribute:
    def __get__(self, instance, owner):
        return instance.__dict__.get(self.name)

    def __set__(self, instance, value):
        print(f"Setting {self.name} to {value}")
        instance.__dict__[self.name] = value

    def __set_name__(self, owner, name):
        self.name = name

class MyClass:
    attr1 = ControlledAttribute()
    attr2 = ControlledAttribute()

obj = MyClass()
obj.attr1 = "Value 1"
obj.attr2 = "Value 2"
print(obj.attr1, obj.attr2)  # Output: Value 1 Value 2
```

    Setting attr1 to Value 1
    Setting attr2 to Value 2
    Value 1 Value 2
    


```python
class LoggedDescriptor:
    def __get__(self, instance, owner):
        print(f"Accessing {self.name}")
        return instance.__dict__.get(self.name)

    def __set__(self, instance, value):
        print(f"Setting {self.name} to {value}")
        instance.__dict__[self.name] = value

    def __set_name__(self, owner, name):
        self.name = name

class MyClass:
    logged_attr = LoggedDescriptor()

obj = MyClass()
obj.logged_attr = "Testing"
print(obj.logged_attr)
```

    Setting logged_attr to Testing
    Accessing logged_attr
    Testing
    


```python
class Temperature:
    def __get__(self, instance, owner):
        return (instance._celsius * 9/5) + 32  # Convert Celsius to Fahrenheit

    def __set__(self, instance, value):
        instance._celsius = value  # Store value in Celsius

class Weather:
    temperature = Temperature()

weather = Weather()
weather.temperature = 25  # Setting in Celsius
print(weather.temperature)  # Output: 77.0 (Fahrenheit)
```

    77.0
    


```python

```


---
**Score: 10**