## 2024-05-24 - Asyncio Stream Batching Optimization
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()`. This reduces context switching, system calls, and TCP fragmentation, leading to optimal batching performance.
**Action:** Always inspect loops containing `writer.write()` calls and consolidate them using string/byte joining if the total payload is reasonably sized.
