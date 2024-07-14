# Efficient RSA
## Solution
- $ct[i]$ should be quadratic residue if $bit$ was 0 as power would then be even
- Check legendre symbol of $ct[i]$
- If it is 1, append 0 else append 1

## Script
```python
from cipher import ct
from sage.all import *

p = 96517490730367252566551196176049957092195411726055764912412605750547823858339
flag = ''

for i in ct:
    a = Integer(i)
    ls = kronecker_symbol(a, p)
    if ls == 1:
        flag += '0'
    else:
        flag += '1'

print(int(flag, 2).to_bytes(100).decode())
```

## Flag
```
OSCTF{d0_y0U_L0v3_m47H_?_<3}
```