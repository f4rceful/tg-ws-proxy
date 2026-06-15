## 2024-05-18 - [Optimize asyncio stream writes]
**Learning:** In Python asyncio streams, favor joining bytes (`b''.join(...)`) into a single `writer.write()` call rather than looping `write()` calls or using `writelines()` for optimal batching performance. Repeated `write()` calls add significant overhead in asyncio stream handling.
**Action:** Always check `for` loops making repetitive `writer.write()` calls and refactor to construct the payload entirely in memory and issue a single `write()` call, especially on fast hot paths.
