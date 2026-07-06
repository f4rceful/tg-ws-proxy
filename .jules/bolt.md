## 2024-05-15 - Bolt's Journal\n**Learning:** This repo is a Python application using Hatchling.\n**Action:** Started.

## 2026-07-06 - Asyncio Stream Batching
**Learning:** In Python `asyncio` streams, using `b''.join(...)` to build a single byte string before calling `writer.write()` is significantly more performant than calling `write()` in a loop for each part. This reduces both the number of underlying system calls and the event loop overhead.
**Action:** Always batch writes into a single byte string when sending multiple items via asyncio streams.
