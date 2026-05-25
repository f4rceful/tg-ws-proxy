## 2024-05-18 - asyncio Stream Writer Batching
**Learning:** Python's `asyncio` `writer.write()` can trigger immediate `socket.send()` syscalls. Calling it in a loop for small pieces of data (like WebSocket frames) is a performance anti-pattern due to excessive syscall overhead.
**Action:** When sending a batch of data frames over an asyncio stream, always join them into a single `bytes` object using `b''.join(...)` and make a single `writer.write()` call before calling `writer.drain()`.
