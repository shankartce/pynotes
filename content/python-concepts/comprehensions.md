---
title: Comprehensions
date: 2026-04-15
author: Your Name
cell_count: 1
score: 0
---

```python
# The traditional way to square even numbers
numbers = [1, 2, 3, 4, 5, 6]
squared_evens = []
for n in numbers:
    if n % 2 == 0:
        squared_evens.append(n ** 2)

# The intermediate "Pythonic" way using a List Comprehension
squared_evens_comp = [n ** 2 for n in numbers if n % 2 == 0]
print(f"List Comprehension: {squared_evens_comp}")

# This also works for dictionaries
word_lengths = {word: len(word) for word in ["apple", "banana", "fig"]}
print(f"Dictionary Comprehension: {word_lengths}")
```


---
**Score: 0**