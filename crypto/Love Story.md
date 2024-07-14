# Efficient RSA
## Solution
- Brute force

## Script
```python
tar = "KJOL_T_ZCTS_ZV_CQKLX_NDFKZTUC"

m = ''
for _ in range(len(tar)):
    for i in range(128):
        letter = chr(i)
        if not letter.isalpha():
            c = letter
        else:
            temp = ord(letter) - 65
            c = chr((temp + _) % 26 + 65)
        if c == tar[_]:
            m += letter
            break

print(m)
```

## Flag
```
OSCTF{KIMI_O_SUKI_NI_NATTE_SHIMATTA.}
```