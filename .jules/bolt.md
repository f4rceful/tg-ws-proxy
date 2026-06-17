## 2026-06-17 - Optimize asyncio batch writes
**Learning:** In Python asyncio streams, calling `writer.write()` inside a loop for multiple chunks adds significant overhead per call, and `writelines()` isn't always optimal.
**Action:** Favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls for optimal batching performance, as seen in `proxy/raw_websocket.py`.
