## 2026-05-29 - Asyncio Stream Writer Optimization
**Learning:** In Python asyncio, looping to write multiple chunks of data to a stream writer is significantly slower than joining the chunks (e.g., using `b''.join()`) and making a single `write()` call.
**Action:** When batching network sends in Python asyncio, always join the byte frames together before writing them.
## 2026-05-30 - Asyncio Stream Writer Optimization Rejection
**Learning:** In Python asyncio, `writer.write()` only buffers data, and the actual syscall happens on `drain()`. Therefore, joining frames with `b''.join()` before a single `write()` call does not reduce syscalls and provides no real performance benefit over calling `write()` in a loop before a single `drain()`.
**Action:** Do not attempt to optimize asyncio `writer.write()` loops using `b''.join()`; rely on `drain()` to handle the actual batching to the network layer.
