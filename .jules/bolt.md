## 2024-05-27 - Batching Asyncio Stream Writes
**Learning:** In Python `asyncio` streams, looping over individual writes (e.g., `for part in parts: writer.write(part)`) creates unnecessary overhead. While `write` is synchronous and buffers, calling it repeatedly for small frames can be less efficient than concatenating bytes and writing once.
**Action:** When handling batches of data to be written to a stream, pre-build the frames and use `b''.join()` to write them in a single `writer.write()` call to reduce function call overhead and batch the buffering operation.

## 2024-05-27 - Asyncio Stream Write Batching Rejected
**Learning:** `writer.write()` in Python's `asyncio` streams only buffers the data in memory. The actual underlying network send (syscall) happens upon `await writer.drain()`. Therefore, joining bytes with `b''.join()` before a single `write()` call doesn't reduce syscalls and provides no real performance benefit compared to calling `write()` in a loop before `drain()`.
**Action:** Do not attempt to optimize multiple `writer.write()` calls using `b''.join()` if they are followed by a single `drain()`, as the behavior and performance are essentially equivalent.
