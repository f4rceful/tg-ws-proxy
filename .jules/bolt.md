## 2024-05-18 - asyncio Stream Writer Batching
**Learning:** Python's `asyncio` `writer.write()` can trigger immediate `socket.send()` syscalls. Calling it in a loop for small pieces of data (like WebSocket frames) is a performance anti-pattern due to excessive syscall overhead.
**Action:** When sending a batch of data frames over an asyncio stream, always join them into a single `bytes` object using `b''.join(...)` and make a single `writer.write()` call before calling `writer.drain()`.

## 2024-05-18 - asyncio Stream Writer Batching Rejection
**Learning:** `writer.write()` in Python's `asyncio` only buffers data in memory. The actual network send (syscall) only happens upon `writer.drain()`. Therefore, replacing multiple `write()` calls in a loop with a single `b''.join()` does not reduce syscalls or improve network I/O performance in any meaningful way.
**Action:** Do not attempt to optimize `writer.write()` calls by manual string/bytes joining before `drain()`, as it's an unnecessary micro-optimization that provides no syscall benefit.
