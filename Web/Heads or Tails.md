# Heads or Tails

## Solution

- Used a custom wordlist of seclists/commons.txt with get- prepended and got the [get-flag](http://34.16.207.52:4789/get-flag) endpoint
- It showed method not allowed so I tried the 'HEAD' http method and it gave the flag.

```bash
curl -X HEAD -i http://34.16.207.52:4789/get-flag
```

## Flag

```
OSCTF{Und3Rr47Ed_H3aD_M3Th0D}
```
