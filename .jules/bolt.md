## 2024-05-01 - Batching write calls in Python asyncio streams
**Learning:** In Python asyncio streams, favor joining bytes (b''.join(...)) into a single writer.write() call rather than looping write() calls or using writelines() for optimal batching performance.
**Action:** Always batch write calls when sending multiple chunks sequentially.
