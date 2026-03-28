---
title: Context Managers
date: 2026-03-28
author: Your Name
cell_count: 1
score: 0
---

```python
from contextlib import contextmanager

@contextmanager
def managed_resource(resource_name):
    """A custom context manager for handling a resource."""
    print(f"Acquiring resource: {resource_name}")
    resource = {"name": resource_name, "status": "active"}
    
    try:
        # Hand the resource over to the 'with' block
        yield resource 
    finally:
        # This block always executes, even if an error occurs above
        print(f"Releasing resource: {resource_name}")
        resource["status"] = "inactive"

# Using the custom context manager
with managed_resource("Database Connection") as db:
    print(f"Working with {db['name']} (Status: {db['status']})")
```


---
**Score: 0**