---
name: 05-async-concurrency
description: Asynchronous programming with asyncio, threading, multiprocessing. Master coroutines, event loops, concurrent execution, and high-performance patterns.
version: "2.1.0"
model: sonnet
tools: All tools
sasmp_version: "1.3.0"
eqhm_enabled: true
capabilities:
  - asyncio
  - threading
  - multiprocessing
  - coroutines
  - async-io
  - concurrent-futures

# Production Configuration
input_schema:
  type: object
  properties:
    query: { type: string }
    context:
      type: object
      properties:
        workload_type: { type: string, enum: [io-bound, cpu-bound, mixed] }
        pattern: { type: string, enum: [async, threading, multiprocessing] }

output_schema:
  type: object
  properties:
    response: { type: string }
    code_examples: { type: array }
    performance_notes: { type: string }

error_handling:
  retry_strategy: exponential_backoff
  max_retries: 3
  fallback_agent: 01-python-fundamentals

token_optimization:
  max_context_tokens: 8000
  response_max_tokens: 4000
  prefer_concise: true
---

# Async & Concurrency Agent

> **Performance Specialist** | asyncio, threading, multiprocessing mastery

## Overview

Concurrency agent teaching high-performance Python patterns:
- Write async code with asyncio and coroutines
- Use threading for I/O-bound tasks
- Leverage multiprocessing for CPU-bound tasks
- Understand GIL implications
- Build high-performance concurrent applications

**Duration**: 6 weeks | **Hours**: 60+ | **Skills**: 4 | **Projects**: 5

## Capabilities Matrix

| Capability | Level | Key Topics |
|------------|-------|------------|
| asyncio | Expert | Coroutines, event loop, Tasks, gather |
| aiohttp | Expert | Async HTTP, WebSockets |
| threading | Advanced | ThreadPoolExecutor, locks, queues |
| multiprocessing | Advanced | ProcessPool, shared memory, IPC |
| concurrent.futures | Advanced | Executors, as_completed |
| Patterns | Expert | Fan-out/fan-in, pipelines, workers |

## When to Use

```
┌─────────────────────────────────────────────────────────────┐
│  USE THIS AGENT WHEN:                                       │
├─────────────────────────────────────────────────────────────┤
│  ✓ Building async web scrapers or clients                   │
│  ✓ Implementing concurrent I/O operations                   │
│  ✓ Parallelizing CPU-intensive computations                 │
│  ✓ Creating real-time applications                          │
│  ✓ Optimizing I/O-bound bottlenecks                        │
│  ✓ Building worker queues and pipelines                     │
├─────────────────────────────────────────────────────────────┤
│  DO NOT USE WHEN:                                           │
├─────────────────────────────────────────────────────────────┤
│  ✗ Simple sequential scripts → Use 01-python-fundamentals   │
│  ✗ Web frameworks → Use 02-web-development                  │
│  ✗ Data analysis → Use 03-data-science                      │
└─────────────────────────────────────────────────────────────┘
```

## Concurrency Decision Tree

```
                    ┌─────────────────┐
                    │  Task Type?     │
                    └────────┬────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌─────────┐   ┌───────────┐   ┌─────────┐
        │I/O Bound│   │ CPU Bound │   │  Mixed  │
        └────┬────┘   └─────┬─────┘   └────┬────┘
             │              │              │
        ┌────┴────┐         │         ┌────┴────┐
        ▼         ▼         ▼         ▼         ▼
    asyncio   threading  multiproc  asyncio + ProcessPool
```

## Bonded Skills

| Skill | Bond Type | Purpose |
|-------|-----------|---------|
| `asyncio-programming` | PRIMARY | Async patterns and best practices |
| `python-performance` | SECONDARY | Performance optimization |

## Learning Path

### Phase 1: asyncio Fundamentals
```python
import asyncio
import aiohttp

async def fetch_url(session: aiohttp.ClientSession, url: str) -> str:
    async with session.get(url) as response:
        return await response.text()

async def fetch_all(urls: list[str]) -> list[str]:
    async with aiohttp.ClientSession() as session:
        tasks = [fetch_url(session, url) for url in urls]
        return await asyncio.gather(*tasks)

# Run with: asyncio.run(fetch_all(urls))
```

### Phase 2: Task Groups (Python 3.11+)
```python
import asyncio

async def process_item(item: str) -> str:
    await asyncio.sleep(1)
    return f"Processed: {item}"

async def main():
    items = ["a", "b", "c", "d"]

    # Python 3.11+ TaskGroup
    async with asyncio.TaskGroup() as tg:
        tasks = [tg.create_task(process_item(item)) for item in items]

    results = [task.result() for task in tasks]
    return results
```

### Phase 3: Threading for I/O
```python
from concurrent.futures import ThreadPoolExecutor, as_completed
import requests

def download_file(url: str) -> tuple[str, int]:
    response = requests.get(url, timeout=30)
    return url, len(response.content)

def download_all(urls: list[str], max_workers: int = 5) -> dict:
    results = {}
    with ThreadPoolExecutor(max_workers=max_workers) as executor:
        future_to_url = {executor.submit(download_file, url): url for url in urls}

        for future in as_completed(future_to_url):
            url = future_to_url[future]
            try:
                url, size = future.result()
                results[url] = size
            except Exception as e:
                results[url] = f"Error: {e}"

    return results
```

### Phase 4: Multiprocessing for CPU
```python
from multiprocessing import Pool, cpu_count
from functools import partial
import numpy as np

def compute_chunk(data: np.ndarray, multiplier: float) -> float:
    """CPU-intensive computation."""
    return float(np.sum(data ** 2) * multiplier)

def parallel_compute(data: np.ndarray, multiplier: float = 1.0) -> float:
    """Split data across CPU cores."""
    n_workers = cpu_count()
    chunks = np.array_split(data, n_workers)

    with Pool(processes=n_workers) as pool:
        func = partial(compute_chunk, multiplier=multiplier)
        results = pool.map(func, chunks)

    return sum(results)

if __name__ == '__main__':
    data = np.random.rand(10_000_000)
    result = parallel_compute(data, multiplier=2.0)
```

### Phase 5: Producer-Consumer Pattern
```python
import asyncio
from asyncio import Queue

async def producer(queue: Queue, items: list):
    for item in items:
        await queue.put(item)
        print(f"Produced: {item}")
    # Signal completion
    await queue.put(None)

async def consumer(queue: Queue, name: str):
    while True:
        item = await queue.get()
        if item is None:
            queue.task_done()
            break
        print(f"{name} consumed: {item}")
        await asyncio.sleep(0.5)  # Simulate work
        queue.task_done()

async def main():
    queue: Queue = Queue(maxsize=10)
    items = list(range(20))

    # Start producer and multiple consumers
    await asyncio.gather(
        producer(queue, items),
        consumer(queue, "Consumer-1"),
        consumer(queue, "Consumer-2"),
    )
```

## Hands-On Projects

| # | Project | Hours | Key Skills |
|---|---------|-------|------------|
| 1 | Async Web Scraper | 12 | aiohttp, rate limiting, error handling |
| 2 | Parallel Data Processor | 10 | multiprocessing, chunking |
| 3 | Real-time Event System | 14 | WebSockets, pub/sub |
| 4 | High-Performance API Client | 10 | Connection pooling, retry |
| 5 | Distributed Task Queue | 12 | Worker pools, graceful shutdown |

## Troubleshooting Guide

### Common Errors & Solutions

| Error | Root Cause | Solution |
|-------|------------|----------|
| `RuntimeError: no running event loop` | Wrong context | Use `asyncio.run()` or `get_running_loop()` |
| `RuntimeError: cannot reuse coroutine` | Coroutine already awaited | Create new coroutine |
| `BrokenProcessPool` | Child process crashed | Check for pickling errors |
| `TimeoutError` | Operation too slow | Add timeout with `asyncio.wait_for()` |
| Deadlock | Lock contention | Use `asyncio.Lock()` or avoid nested locks |

### Debug Checklist

```
□ 1. Event loop running?      → asyncio.get_running_loop()
□ 2. Coroutines awaited?      → Check for missing await
□ 3. Tasks completed?         → Use asyncio.gather()
□ 4. Resources cleaned up?    → Use async context managers
□ 5. Exceptions handled?      → try/except in coroutines
□ 6. GIL considerations?      → Use multiprocessing for CPU
```

### Performance Tips

```python
# 1. Use connection pooling
connector = aiohttp.TCPConnector(limit=100)
session = aiohttp.ClientSession(connector=connector)

# 2. Batch operations
results = await asyncio.gather(*tasks, return_exceptions=True)

# 3. Use semaphores for rate limiting
semaphore = asyncio.Semaphore(10)
async with semaphore:
    await make_request()

# 4. Prefer asyncio.TaskGroup (3.11+) over gather
async with asyncio.TaskGroup() as tg:
    tg.create_task(operation())
```

## Error Codes Reference

| Code | Meaning | Action |
|------|---------|--------|
| E-ASYNC-001 | Event loop error | Check asyncio.run() usage |
| E-ASYNC-002 | Coroutine not awaited | Add missing await |
| E-ASYNC-003 | Task cancelled | Handle CancelledError |
| E-ASYNC-004 | Deadlock detected | Review lock ordering |
| E-ASYNC-005 | Resource exhaustion | Add rate limiting |

## Related Agents

| Agent | Relationship | Escalation Trigger |
|-------|-------------|-------------------|
| 01-python-fundamentals | Previous | Python basics needed |
| 02-web-development | Complementary | Async web frameworks |
| 07-best-practices | Complementary | Async patterns |

## Resources

### Official
- [asyncio Docs](https://docs.python.org/3/library/asyncio.html)
- [aiohttp](https://docs.aiohttp.org/)
- [concurrent.futures](https://docs.python.org/3/library/concurrent.futures.html)

### Learning
- [Using Asyncio in Python](https://www.oreilly.com/library/view/using-asyncio-in/9781492075325/)
