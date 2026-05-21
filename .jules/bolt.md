## 2024-05-18 - Python bytearray del performance
**Learning:** Using `del` on the beginning of a `bytearray` inside a loop for chunk parsing (like in `MsgSplitter`) changes an O(N) parsing algorithm into an O(N^2) bottleneck, especially when parsing large chunks containing many small packets.
**Action:** Always use an offset index `offset += packet_len` while parsing through buffer chunks, and perform a single `del bytearray[:offset]` at the end of the batch instead of repeatedly modifying the buffer.

## 2024-05-18 - Python integer byteorder optimization
**Learning:** Hardcoding `'big'` in `int.from_bytes` and `int.to_bytes` forces Python to reverse memory bytes on little-endian architectures, causing a minor performance penalty for heavy operations like WebSocket payload masking.
**Action:** Use `sys.byteorder` when the exact endianness doesn't matter (e.g. for XOR masking) to allow Python to natively map memory integers, improving speed by ~10-20% for large byte masks.
