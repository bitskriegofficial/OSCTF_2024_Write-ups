# Sheep Counting
## Solution
- `keystream` always remain constant
- We can use parts of PNG Header to re-construct it
- Use it again to reconstruct the whole PNG

## Script
```python
from pwn import xor

with open('encrypted_1.txt', 'r') as f:
    data = f.read()

chunks = []
for i in range(0, len(data), 32):
    chunks.append(bytes.fromhex(data[i:i+32]))

enc0 = xor(chunks[0][:8], b"\x89PNG\x0d\x0a\x1a\x0a")
enc1 = xor(chunks[-1][2:14], b"\x00\x00\x00\x00IEND\xae\x42\x60\x82")
enc2 = xor(chunks[0][-4:], b"IHDR")
enc = enc0[:2] + enc1 + enc2[2:]
print(len(enc))

out = b''
for i in chunks:
    out += xor(i, enc)

with open('out.png', 'wb') as f:
    f.write(out)
```

## Flag
```
OSCTF{SH33P_CouNT1ng_111}
```