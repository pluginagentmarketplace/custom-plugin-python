---
description: Asynchronous programming with asyncio, threading, and multiprocessing. Master coroutines, event loops, concurrent execution, parallel processing, and async I/O for high-performance Python applications.
capabilities: ["asyncio", "threading", "multiprocessing", "coroutines", "async-io", "concurrent-futures"]
---

# Async Programming & Concurrency

## Overview

Agent 5 teaches asynchronous and concurrent programming in Python:
- Write async code with asyncio and coroutines
- Use threading for I/O-bound tasks
- Leverage multiprocessing for CPU-bound tasks
- Understand the GIL and its implications
- Build high-performance concurrent applications

**Duration**: 6 weeks | **Learning Hours**: 60+ | **Skills**: 4 | **Projects**: 5

## Capabilities

This agent specializes in:
- **asyncio**: Coroutines, event loop, async/await, Tasks, Futures
- **aiohttp**: Async HTTP client/server, websockets
- **threading**: Thread creation, synchronization, thread pools
- **multiprocessing**: Process pools, shared memory, inter-process communication
- **concurrent.futures**: ThreadPoolExecutor, ProcessPoolExecutor
- **Async patterns**: Fan-out/fan-in, pipelines, worker queues

## Skills Covered

### Skill 1: asyncio Fundamentals
```python
import asyncio
import aiohttp

async def fetch_url(session, url):
    async with session.get(url) as response:
        return await response.text()

async def main():
    urls = ['https://example.com', 'https://python.org']
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
    return results

# Run async code
asyncio.run(main())
```

### Skill 2: Threading for I/O
```python
import threading
from concurrent.futures import ThreadPoolExecutor
import requests

def download_file(url):
    response = requests.get(url)
    filename = url.split('/')[-1]
    with open(filename, 'wb') as f:
        f.write(response.content)
    return filename

# Using ThreadPoolExecutor
urls = ['https://example.com/file1.zip', 'https://example.com/file2.zip']
with ThreadPoolExecutor(max_workers=5) as executor:
    results = executor.map(download_file, urls)
```

### Skill 3: Multiprocessing for CPU
```python
from multiprocessing import Pool, cpu_count
import numpy as np

def compute_intensive(data):
    # CPU-bound operation
    return np.sum(data ** 2)

if __name__ == '__main__':
    # Create large datasets
    datasets = [np.random.rand(1000000) for _ in range(cpu_count())]

    # Parallel processing
    with Pool(processes=cpu_count()) as pool:
        results = pool.map(compute_intensive, datasets)
```

### Skill 4: Async Patterns
```python
async def worker(name, queue):
    while True:
        task = await queue.get()
        if task is None:
            break
        print(f"{name} processing {task}")
        await asyncio.sleep(1)  # Simulate work
        queue.task_done()

async def producer_consumer():
    queue = asyncio.Queue()

    # Start workers
    workers = [
        asyncio.create_task(worker(f"Worker-{i}", queue))
        for i in range(3)
    ]

    # Add tasks
    for i in range(10):
        await queue.put(f"Task-{i}")

    # Wait for completion
    await queue.join()

    # Stop workers
    for _ in workers:
        await queue.put(None)
    await asyncio.gather(*workers)
```

## Hands-On Projects

1. **Async Web Scraper** (12 hours)
2. **Parallel Data Processor** (10 hours)
3. **Real-time Event System** (14 hours)
4. **High-Performance API Client** (10 hours)
5. **Distributed Task Queue** (12 hours)

## Assessment

- [ ] Write efficient async code
- [ ] Choose correct concurrency model
- [ ] Handle thread synchronization
- [ ] Optimize CPU-bound tasks
