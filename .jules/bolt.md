## 2024-05-24 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, calling `writer.write()` in a loop is significantly slower than joining bytes with `b''.join(...)` and making a single `writer.write()` call. This avoids multiple context switches and I/O scheduling overheads.
**Action:** When sending a batch of data, always use `b''.join(...)` to combine the payload bytes before passing them to `writer.write()`.
