# The Broken Sword

## Analysis
We see that the script is comprised of all reversible operations.

## Solution
We reverse the operations in the reverse order as that of the script. At the time of the challenge I did this entirely in the python interactive shell. Here's an excerpt from by `.python_history`
```python
>>> from Crypto.Util.number import bytes_to_long
>>> bytes_to_long(b'\x0c\x07\x9e\x8e/\xc2')
>>> ord('a')
>>> 97+23
>>> chr(120)
>>> f = 5483762481^120
>>> g = f * 35
>>> v = f ^ 34
>>> al = 899433952965498
>>> h = 0.0028203971921452278
>>> h * 4567234567342
>>> h / 3.14159
>>> h ^ 34
>>> h * 4567234567342
>>> 12881415549.6 / 3.14
>>> 4102361640 ^ 34
>>> 4102361610 / 30
>>> v2 = 136745387
>>> al /= 67
>>> g+v2+f
>>> al -= 197552195567
>>> al
>>> a
>>> z1
>>> z
>>> 13226864422850-13226835162127
>>> v2
```

## Flag
```
OSCTF{29260723_13226835162127_136745387}
```
