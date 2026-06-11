## 2024-05-19 - Batching Asyncio Stream Writes
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()`. Doing so significantly reduces overhead and optimizes batching performance.
**Action:** Always batch writes together into a single `write()` call when dealing with asynchronous stream operations, especially within `send_batch` or similar batch-processing methods.
