## 2024-06-25 - Python Bytearray Repeated Shrinking Anti-pattern
**Learning:** In `MsgSplitter.split()`, deleting a slice from the beginning of a `bytearray` inside a loop (`del self._cipher_buf[:packet_len]`) causes an O(N) memory shift for each deletion. When receiving a large chunk containing many small packets, this turns into an O(N^2) bottleneck.
**Action:** Use an offset variable to iterate through the bytearray buffer without mutating it. Only slice or `del` the processed portion of the buffer once at the end of the method.
