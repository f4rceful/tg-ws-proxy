## 2026-07-02 - Asyncio Stream Write Batching
**Learning:** In Python asyncio streams, calling `writer.write()` multiple times in a loop can cause significant overhead compared to joining the bytes first, as each `write()` call might trigger transport layer operations and context switches.
**Action:** Favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
