# seed sPRING

## Analysis
On decompilation, we see that the binary is randomly generating 30 numbers based on the seed of `time(NULL)`. Accounting for the time it takes to establish connection using nc, we can guess the offset for the seed from the current time of our device.

## Solution
I wrote a C program to generate random numbers using the seed for the next second, which seemed to work fine. (NOTE: the second offset might be different for you)
```c
srand(time(NULL)+1);
for (int i = 0; i < 30; i++) {
    printf("%d\n", rand() & 15);
}
```

I, then just piped the output of this into the remote.
```
└─$ ./a.out | nc 34.125.199.248 2534
```

## Flag
```
OSCTF{th1s_w4snt_phys1cs_lm4o}
```
