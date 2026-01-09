---
title: Data Classes
date: 2026-01-09
author: Your Name
cell_count: 11
score: 10
---

```python
from dataclasses import dataclass

@dataclass
class Person:
    name: str
    age: int

person = Person(name="Alice", age=30)
print(person)  # Output: Person(name='Alice', age=30)
```

    Person(name='Alice', age=30)
    


```python
from dataclasses import dataclass

@dataclass
class Book:
    title: str
    author: str
    price: float = 9.99

book = Book(title="Python 101", author="John Doe")
print(book)  # Output: Book(title='Python 101', author='John Doe', price=9.99)
```

    Book(title='Python 101', author='John Doe', price=9.99)
    


```python
from dataclasses import dataclass

@dataclass(frozen=True)
class Point:
    x: int
    y: int

point = Point(3, 4)
print(point)  # Output: Point(x=3, y=4)

# point.x = 5  # Raises error: FrozenInstanceError
```

    Point(x=3, y=4)
    


```python
from dataclasses import dataclass

@dataclass
class Rectangle:
    width: float
    height: float
    area: float = 0.0

    def __post_init__(self):
        self.area = self.width * self.height

rect = Rectangle(width=5, height=10)
print(rect.area)  # Output: 50.0
```

    50
    


```python
from dataclasses import dataclass

@dataclass
class Item:
    name: str
    price: float

item1 = Item(name="Laptop", price=1000.0)
item2 = Item(name="Laptop", price=1000.0)

print(item1 == item2)  # Output: True
```

    True
    


```python
from dataclasses import dataclass, field
from typing import List

@dataclass
class ShoppingCart:
    items: List[str] = field(default_factory=list)

cart = ShoppingCart()
cart.items.append("Apple")
print(cart)  # Output: ShoppingCart(items=['Apple'])
```

    ShoppingCart(items=['Apple'])
    


```python
from dataclasses import dataclass

@dataclass
class User:
    username: str
    password: str = "secret"

    def __repr__(self):
        return f"User(username='{self.username}')"

user = User(username="john_doe")
print(user)  # Output: User(username='john_doe')
```

    User(username='john_doe')
    


```python
from dataclasses import dataclass
from typing import List

@dataclass
class Classroom:
    students: List[str]
    teacher: str

classroom = Classroom(students=["Alice", "Bob"], teacher="Mr. Smith")
print(classroom)  # Output: Classroom(students=['Alice', 'Bob'], teacher='Mr. Smith')
```

    Classroom(students=['Alice', 'Bob'], teacher='Mr. Smith')
    


```python
from dataclasses import dataclass

@dataclass
class Animal:
    name: str

@dataclass
class Dog(Animal):
    breed: str

dog = Dog(name="Buddy", breed="Golden Retriever")
print(dog)  # Output: Dog(name='Buddy', breed='Golden Retriever')
```

    Dog(name='Buddy', breed='Golden Retriever')
    


```python
from dataclasses import dataclass, asdict, astuple

@dataclass
class Employee:
    name: str
    role: str
    salary: float

employee = Employee(name="Alice", role="Developer", salary=75000.0)
print(asdict(employee))  # Output: {'name': 'Alice', 'role': 'Developer', 'salary': 75000.0}
print(astuple(employee))  # Output: ('Alice', 'Developer', 75000.0)
```

    {'name': 'Alice', 'role': 'Developer', 'salary': 75000.0}
    ('Alice', 'Developer', 75000.0)
    


```python

```


---
**Score: 10**