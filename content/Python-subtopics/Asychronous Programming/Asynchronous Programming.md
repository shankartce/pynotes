---
title: Asynchronous Programming
date: 2026-01-09
author: Your Name
cell_count: 11
score: 10
---

```python
import asyncio

async def say_hello():
    print("Hello, World!")
    await asyncio.sleep(1)
    print("Goodbye, World!")

await(say_hello())
```

    Hello, World!
    Goodbye, World!
    


```python
import asyncio

async def task1():
    print("Task 1 starting...")
    await asyncio.sleep(2)
    print("Task 1 done!")

async def task2():
    print("Task 2 starting...")
    await asyncio.sleep(1)
    print("Task 2 done!")

async def main():
    await asyncio.gather(task1(), task2())

await(main())
```

    Task 1 starting...
    Task 2 starting...
    Task 2 done!
    Task 1 done!
    


```python
import asyncio

async def countdown(n: int):
    while n > 0:
        print(f"Counting down: {n}")
        await asyncio.sleep(2)
        n -= 1
    print("Countdown finished!")

await(countdown(5))


```

    Counting down: 5
    Counting down: 4
    Counting down: 3
    Counting down: 2
    Counting down: 1
    Countdown finished!
    


```python
import aiohttp
import asyncio

async def fetch_url(session, url):
    async with session.get(url) as response:
        return await response.text()

async def main():
    urls = ["https://example.com", "https://httpbin.org", "https://python.org"]
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        for i, content in enumerate(results):
            print(f"Content from URL {i + 1}:\n{content[:100]}...\n")

await(main())
```

    Content from URL 1:
    <!doctype html><html lang="en"><head><title>Example Domain</title><meta name="viewport" content="wid...
    
    Content from URL 2:
    <!DOCTYPE html>
    <html lang="en">
    
    <head>
        <meta charset="UTF-8">
        <title>httpbin.org</title>
     ...
    
    Content from URL 3:
    <!doctype html>
    <!--[if lt IE 7]>   <html class="no-js ie6 lt-ie7 lt-ie8 lt-ie9">   <![endif]-->
    <!-...
    
    


```python
import asyncio

async def producer(queue):
    for i in range(5):
        print(f"Producing {i}")
        await queue.put(i)
        await asyncio.sleep(1)

async def consumer(queue):
    while True:
        item = await queue.get()
        print(f"Consuming {item}")
        queue.task_done()

async def main():
    queue = asyncio.Queue()

    consumer_task = asyncio.create_task(consumer(queue))
    await producer(queue)

    consumer_task.cancel()

await(main())
```

    Producing 0
    Consuming 0
    Producing 1
    Consuming 1
    Producing 2
    Consuming 2
    Producing 3
    Consuming 3
    Producing 4
    Consuming 4
    


```python
import asyncio

async def slow_task():
    await asyncio.sleep(2.1)
    return "Task completed!"

async def main():
    try:
        result = await asyncio.wait_for(slow_task(), timeout=2)
        print(result)
    except asyncio.TimeoutError:
        print("Task timed out!")

await(main())
```

    Task timed out!
    


```python
import aiofiles
import asyncio

async def write_to_file():
    async with aiofiles.open("example.txt", "w") as f:
        await f.write("Hello, Async File I/O!\n")

async def read_from_file():
    async with aiofiles.open("example.txt", "r") as f:
        content = await f.read()
        print(content)

async def main():
    await write_to_file()
    await read_from_file()

await(main())
```

    Hello, Async File I/O!
    
    


```python
import asyncio

async def limited_task(sem, i):
    async with sem:
        print(f"Task {i} starting...")
        await asyncio.sleep(2)
        print(f"Task {i} done!")

async def main():
    sem = asyncio.Semaphore(2)  # Limit to 2 concurrent tasks
    tasks = [limited_task(sem, i) for i in range(5)]
    await asyncio.gather(*tasks)

await(main())
```

    Task 0 starting...
    Task 1 starting...
    Task 0 done!
    Task 1 done!
    Task 2 starting...
    Task 3 starting...
    Task 2 done!
    Task 3 done!
    Task 4 starting...
    Task 4 done!
    


```python
import asyncio

async def print_numbers():
    for i in range(5):
        print(f"Number: {i}")
        await asyncio.sleep(1)

async def main():
    task = asyncio.create_task(print_numbers())
    print("Task created. Doing something else...")
    await asyncio.sleep(3)
    print("Main task completed.")
    await task

await(main())
```

    Task created. Doing something else...
    Number: 0
    Number: 1
    Number: 2
    Main task completed.
    Number: 3
    Number: 4
    


```python
import asyncio

async def producer(queue):
    for i in range(5):
        print(f"Producer: putting {i} in queue")
        await queue.put(i)
        await asyncio.sleep(1)

async def consumer(queue):
    while True:
        item = await queue.get()
        print(f"Consumer: got {item} from queue")
        queue.task_done()

async def main():
    queue = asyncio.Queue()
    await asyncio.gather(producer(queue), consumer(queue))

await(main())
```

    Producer: putting 0 in queue
    Consumer: got 0 from queue
    Producer: putting 1 in queue
    Consumer: got 1 from queue
    Producer: putting 2 in queue
    Consumer: got 2 from queue
    Producer: putting 3 in queue
    Consumer: got 3 from queue
    Producer: putting 4 in queue
    Consumer: got 4 from queue
    


```python

```


---
**Score: 10**