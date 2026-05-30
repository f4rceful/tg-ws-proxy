## 2025-02-23 - [WebSocket Batch Send]
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Use `b''.join()` along with list comprehension to prepare the full payload buffer before calling `writer.write`.
