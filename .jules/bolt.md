## 2024-05-19 - Batching Asyncio Stream Writes
**Learning:** In Python asyncio `StreamWriter`, each `write()` call incurs transport validation and state-checking overhead before data even reaches the underlying socket buffer. Looping over many small frames to write them individually inside WebSocket batches leads to unnecessary context switches and CPU overhead.
**Action:** Always prefer joining byte strings (e.g. `b''.join(...)`) in memory and submitting a single, concatenated payload to `writer.write()` to minimize execution overhead in fast-path streaming operations.
