# Efficient RSA
## Solution
- Small $n$
- Factorize $n$ to get $p$ and $q$

## Script
```python
n = 13118792276839518668140934709605545144220967849048660605948916761813
e = 65537
c = 8124539402402728939748410245171419973083725701687225219471449051618

p = 3058290486427196148217508840815579
q = n // p

phi = (p - 1) * (q - 1)
d = pow(e, -1, phi)
m = pow(c, d, n)
print(m.to_bytes(100).decode())
```

## Flag
```
OSCTF{F4ct0r1Ng_F0r_L1f3}
```