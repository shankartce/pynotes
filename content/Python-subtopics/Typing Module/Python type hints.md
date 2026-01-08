---
title: Python Type Hints
date: 2026-01-08
author: Your Name
cell_count: 11
score: 10
---

```python
from typing import List

def sum_of_integers(numbers: List[int]) -> int:
    return sum(numbers)

print(sum_of_integers([1, 2, 3]))  # Output: 6
```

    6
    


```python
from typing import Optional

def greet(name: Optional[str] = None) -> str:
    if name:
        return f"Hello, {name}!"
    return "Hello, Guest!"

print(greet())           # Output: Hello, Guest!
print(greet("Alice"))    # Output: Hello, Alice!
```

    Hello, Guest!
    Hello, Alice!
    


```python
from typing import Dict

def count_fruits(fruit_counts: Dict[str, int]) -> int:
    return sum(fruit_counts.values())

fruits = {"apple": 5, "banana": 3, "orange": 2}
print(count_fruits(fruits))  # Output: 10
```

    10
    


```python
from typing import Union

def square_or_length(value: Union[int, str]) -> int:
    if isinstance(value, int):
        return value ** 2
    return len(value)

print(square_or_length(4))       # Output: 16
print(square_or_length("test"))  # Output: 4
```

    16
    4
    


```python
from typing import List

Vector = List[float]

def dot_product(vec1: Vector, vec2: Vector) -> float:
    return sum(x * y for x, y in zip(vec1, vec2))

print(dot_product([1.0, 2.0], [3.0, 4.0]))  # Output: 11.0
```

    11.0
    


```python
from typing import Callable

def apply_operation(a: int, b: int, operation: Callable[[int, int], int]) -> int:
    return operation(a, b)

result = apply_operation(2, 3, lambda x, y: x + y)
print(result)  # Output: 5
```

    5
    


```python
from typing import Tuple

def process_coordinates(coords: Tuple[float, float]) -> str:
    return f"Latitude: {coords[0]}, Longitude: {coords[1]}"

print(process_coordinates((40.7128, -74.0060)))
# Output: Latitude: 40.7128, Longitude: -74.006
```

    Latitude: 40.7128, Longitude: -74.006
    


```python
from typing import Any

def stringify(value: Any) -> str:
    return str(value)

print(stringify(42))         # Output: '42'
print(stringify([1, 2, 3]))  # Output: '[1, 2, 3]'
```

    42
    [1, 2, 3]
    


```python
from typing import Literal

def choose_plan(plan: Literal["free", "premium", "enterprise"]) -> str:
    return f"You selected the {plan} plan."

print(choose_plan("premium"))  # Output: You selected the premium plan.
```

    You selected the premium plan.
    


```python
from typing import TypedDict

class User(TypedDict):
    name: str
    age: int
    email: str

def display_user(user: User) -> str:
    return f"{user['name']} ({user['age']}) can be reached at {user['email']}."

user = {"name": "Alice", "age": 30, "email": "alice@example.com"}
print(display_user(user))
# Output: Alice (30) can be reached at alice@example.com.
```

    Alice (30) can be reached at alice@example.com.
    


```python

```


---
**Score: 10**