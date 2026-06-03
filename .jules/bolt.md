## 2025-02-20 - [Batching asyncio writes]
**Learning:** In Python asyncio streams, calling `writer.write()` multiple times in a loop results in expensive multiple socket `send()` system calls.
**Action:** Always favor joining bytes into a single payload using `b''.join(...)` and a single `write()` call when sending batches of data to minimize system call overhead.
