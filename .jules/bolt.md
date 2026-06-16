## 2024-06-16 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, calling `writer.write()` in a loop creates significant overhead compared to joining the bytes first. While `writelines()` exists, joining with `b''.join()` and using a single `write()` call is often more performant and robust for batching websocket frames.
**Action:** When batching multiple binary frames or payloads for asyncio `StreamWriter`, favor using `b''.join()` to create a single payload before calling `writer.write()`.
