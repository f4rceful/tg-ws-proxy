## 2024-05-24 - Asyncio Writer Batching
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** Always batch I/O operations by concatenating bytes in memory when possible instead of making multiple syscalls or writer loop calls.
