## 2024-06-21 - Optimize asyncio stream writes using b''.join
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance. This reduces syscalls and asyncio task overhead.
**Action:** When handling batches of data to be sent over asyncio streams, construct a list of bytes and join them before a single `write` call.
