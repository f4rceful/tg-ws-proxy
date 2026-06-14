## 2024-06-14 - [Batching asyncio stream writes]
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance.
**Action:** When sending a batch of frames in `send_batch` in `proxy/raw_websocket.py`, combine the frames using `b"".join()` before calling `self.writer.write()` to avoid multiple write syscalls and optimize batching.
