## 2024-05-20 - [Batching asyncio stream writes]
**Learning:** In Python asyncio streams, looping `write()` calls or using `writelines()` has significant overhead compared to executing a single `writer.write()` call with concatenated bytes. Batching stream writes into a single large byte string (`b''.join(...)`) is highly beneficial for performance.
**Action:** Always favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls when dealing with multiple frames or chunks.
