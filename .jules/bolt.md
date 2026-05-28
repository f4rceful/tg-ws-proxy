## 2026-05-28 - [Optimize asyncio stream batching]
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** When sending batches of frames or messages, always pre-calculate the byte frames, join them, and write them in a single call.
