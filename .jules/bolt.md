## 2026-05-29 - Asyncio Stream Writer Optimization
**Learning:** In Python asyncio, looping to write multiple chunks of data to a stream writer is significantly slower than joining the chunks (e.g., using `b''.join()`) and making a single `write()` call.
**Action:** When batching network sends in Python asyncio, always join the byte frames together before writing them.
