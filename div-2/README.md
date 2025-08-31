# Div-2

Description: Some might call this a programming challenge...

My approach: The source code was given to us, so firstly I had to figure out how the code worked. The code first generated a random number (= x) between 1 to 2^128. It then asked for an input, where I had to "guess" the number (let my guess be y), and it outputted floor(x/y). Hence if x<y, it outputs 0, and 1 otherwise. This immediately reminded me of binary search but on a much larger scale, hence manual computation would not work. I wrote a code in Python whose logic is shown below, which does the binary search. During the CTF, the server was working, so I had used socket to establish a connection using the host and port given. Running the code yielded the flag: scriptCTF{b1n4ry_s34rch_u51ng_d1v1s10n?!!}

```python
lo,hi = 1<<127,(1<<128)-1
while lo<=hi:
    mid = (lo+hi+1)//2
    print(f"1\n{mid}\n")
    ans = int(input())
    if ans==0: hi = mid-1
    else: lo = mid
    print(lo,hi)
secret = lo
print(f"2\n{secret}\n")
flag = input()
print(f"{flag}\n")
```
