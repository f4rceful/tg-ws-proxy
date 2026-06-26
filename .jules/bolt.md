## 2024-05-24 - Python Asyncio Streams Optimization
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance. Multiple `write()` calls create unnecessary overhead and context switches.
**Action:** Always combine small byte payloads before handing them off to the stream writer in performance-sensitive asyncio network code.
