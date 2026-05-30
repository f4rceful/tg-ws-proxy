## 2024-05-26 - Asyncio Stream Batching (Correction)
**Learning:** In Python `asyncio` streams, `writer.write()` merely buffers data in user-space. The actual system call (and resulting overhead) occurs on `await writer.drain()`. Therefore, joining bytes before calling `write()` does not save system calls and offers no meaningful performance advantage over calling `write()` in a loop.
**Action:** Do not manually buffer or join data before `writer.write()` in an attempt to save system calls. Let `asyncio` handle the buffering.
