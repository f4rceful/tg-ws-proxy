## 2024-06-07 - Python Asyncio Stream Batching
**Learning:** In Python asyncio streams, looping `write()` calls or using `writelines()` is slower.
**Action:** Favor joining bytes (`b"".join(...)`) into a single `writer.write()` call for optimal batching performance.
