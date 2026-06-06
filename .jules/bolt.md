## 2024-06-06 - [AsyncIO Stream Batching]
**Learning:** In Python asyncio streams, doing multiple `writer.write()` calls sequentially can create unnecessary transport-level overhead, especially when writing small payload frames from batch splits.
**Action:** When working with asyncio and websocket framing, pre-compute the frames and join them (`b''.join(...)`) before making a single `writer.write()` call to optimize batch processing.
