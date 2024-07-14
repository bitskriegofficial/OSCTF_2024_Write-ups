# The Secret Message
## Solution
- Small $e$
- Compute $\sqrt[3]{ct}$ to get the flag

## Script
```python
from sage.all import *

ct = Integer(123455882152544968263105106204728561055927061837559618140477097078038573915018542652304779417958037315601542697001430243903815208295768006065618427997903855304186888710867473025125)
pt = int(ct.nth_root(3))
print(pt.to_bytes(100).decode())
```

## Flag
```
OSCTF{Cub3_R00Ting_RSA!!}
```