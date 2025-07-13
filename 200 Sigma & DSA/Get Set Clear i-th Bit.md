- **Related Topic :  [[Bit Manipulation]]
- **Created** : July 8, 2025 | 10:46 PM
- *Tags*: #sigma #ShraddhaKhapra 
---
Given a number let say 6 (110) and asked the 2nd bit. bit count runs from the end.
- We need to think of the bit mask and the operation we can perform to find the i-th bit
- Either 0 or 1.
- If we take the binary number where every bit is 0 except the i-th position, and perform the `&` operation. `0&1 = 0` and `1&1 = 1` so if the bit is 0 that will make the number 0 else return something more than 1
### Set
- if i-th bit is 0 set it to 1.
	- Apply `OR`
Clear
- if the i-th bit is 1 set it to 0.
	- Apply `&` to `~(1<<i)`


## Check for Power of 2

```
Power of 2's in binary
2  ->  10
4  ->  100
8  ->  1000
16 ->  10000
32 ->  100000
```
- So the power of 2 has only one bit on and else is off.
```
Binary form 2^n -1
1  -> 1
3  -> 11
7  -> 111
15 -> 1111
31 -> 11111
```
- ***So the $2^n -1$ has all 1's all bit on.***
- So there is perfect mismatch.
###### SO what will be the `4 & 3`
```
  100 
& 011
-------
  000
```
- If a number `num` is a power of 2 and the and operation between `num & (num-1)` will always be 0.
[LC 231](https://leetcode.com/problems/power-of-two/description/)
- There is an edge case for `num = 0` it's not a power of 2 but `0 & -1`

**In General `n & n-1` removes the lowest 1 (set) bit the rightmost 1.**
- This helps to solve the *Hamming Weight* Problem, The count of 1 bit in a num.
- Logic
```pseudo
Iterate through the num till it become 0
while num:
	num = num & num-1
at each iteration rightmost 1 will be 0 and slowly the num will be 0.


n =  12 → 1100
n-1 = 11 → 1011
----------------
n & (n-1) = 1000 → 8

```
This is *Brian Kernighan's Algorithm*

#### Why Does `n & (n - 1)` Remove the Rightmost Set Bit?

1. When you subtract 1 from `n`, you **flip the rightmost 1 to 0** and **flip all 0s after it to 1s**.
2. So `n` and `n-1` differ at the **rightmost set bit**, which becomes 0 in `n & (n - 1)`.
- Suppose `n = 10100`
```
Binary:      1 0 1 0 0   ← original n
             ↓
Subtract 1:  1 0 0 1 1   ← flips the rightmost 1 and all 0s after

AND:         1 0 0 0 0   ← rightmost set bit gone!

```
- Notice how the **rightmost 1 (second position from the right)** is gone!
#### Algorithm Logic Step-by-Step

```python
while n:
  n = n & (n - 1)   # remove the rightmost set bit
  count += 1        # we just removed 1 set bit, so increase count
```

- No of Iteration = No of 1's = Hamming Weight
 - [LC 190 Reverse Bit](https://leetcode.com/problems/reverse-bits/description/)
 - [LC 191 Count of 1's Bit ](https://leetcode.com/problems/number-of-1-bits/description/)
 - 