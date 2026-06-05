## 2024-06-05 - Optimize asyncio write batching
**Learning:** Calling `writer.write()` inside a loop for `send_batch` introduces unnecessary overhead per frame. In Python `asyncio` streams, batching data using `b''.join()` into a single `write()` call is more performant than looping or using `writelines()`.
**Action:** Always favor joining byte sequences into a single `writer.write()` call when sending batches of data over asyncio streams.
