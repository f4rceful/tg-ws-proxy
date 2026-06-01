## 2024-06-01 - [Asyncio Stream Batching]
**Learning:** In Python asyncio streams, looping `write()` calls or using `writelines()` is less efficient than joining bytes and making a single `write()` call.
**Action:** Always favor joining bytes (`b''.join(...)`) into a single `writer.write()` call for optimal batching performance in asyncio code.
