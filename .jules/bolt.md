## 2024-06-30 - Asyncio Stream Batching
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** When sending multiple packets/frames sequentially, aggregate them into a single byte string before calling `writer.write()` to minimize system calls and overhead.
