## 2024-05-30 - [Python writer.writelines vs join]
**Learning:** `writer.write(b''.join(...))` is measurably faster than `writer.writelines(...)` or a loop calling `writer.write` in asyncio streams for this project, especially when batching multiple chunks.
**Action:** Use `b''.join(...)` and `writer.write()` instead of `writer.writelines()` when possible.
