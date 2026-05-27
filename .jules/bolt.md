## 2024-05-27 - Batching Asyncio Stream Writes
**Learning:** In Python `asyncio` streams, looping over individual writes (e.g., `for part in parts: writer.write(part)`) creates unnecessary overhead. While `write` is synchronous and buffers, calling it repeatedly for small frames can be less efficient than concatenating bytes and writing once.
**Action:** When handling batches of data to be written to a stream, pre-build the frames and use `b''.join()` to write them in a single `writer.write()` call to reduce function call overhead and batch the buffering operation.
