- **Prerequisite :  [[Binary Numbers System]]
- **Created** : July 3, 2025 | 1:39 AM
- *Tags*: #sigma #ShraddhaKhapra #DSA 

---
- We know Binary conversions. `Bin2dec` and `dec2Bin`
## Bitwise Operators
- When we apply a bitwise operator on two decimal numbers those numbers converts to *Binary Numbers and then the operations gets applied on those 0 and 1*
- Ex - 3 (0011) 5(0101) 9(1001)
### And (&) Operator
- && means the logical and.
- *Rule* - 1 only when both are 1

|     | AND |     |
| :-: | :-: | :-: |
|  0  |  0  |  0  |
|  0  |  1  |  0  |
|  1  |  0  |  0  |
|  1  |  1  |  1  |
- so for `3 & 5` 
```
3 = 0 0 1 1
5 = 0 1 0 1
-------------
and 0 0 0 1 = 1 (decimal ans)

verify in code

9 = 1001
5 = 0101
----------
ans= 0001 = 1
```

### OR (|) - 
- *Rule* - 0 only when both are 0. Opposite of AND

|     | OR  |     |
| :-: | :-: | :-: |
|  0  |  0  |  0  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  1  |
```
OR
5 = 0101
9 = 1001
----------
or= 1101 = 13
```

### XOR (^)
- Exclusive OR
- *Rule* - 0 for Same bit and 1 for different bits

|     | XOR |     |
| :-: | :-: | :-: |
|  0  |  0  |  0  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  0  |
```
XOR
5 = 0101
9 = 1001
xor= 1100 = 12
```

---
## Binary NOT Operator - [[One's Complement]]
- `tilde ~`
- `~1 = 0` and `~0 = 1`
- For num = 6 (110) so `~6` will be 001 (1)??? - Try
	- This is not 1, it's -7
	- *The reason* being - Any number in memory doesn't get stored in exactly this form (110) in binary but for a system of 32 bits that number will have zeros in all the missing bits.
		- Therefore the *1's Complement* form of 6 becomes `11111001` (for a 8 bit system let say).
		- Now to from this form we calculate the *2's Complement form* to know the actual answer, where the left most num denotes the sign [1 for negative and 0 for positive] called the **Most Significant Bit (MSB)** and apply the not on the rest of bits.
		- 1 1 1 1 1 0 0 1 -> -(0000110 + 1) = -111 = -7
- For num = 0 `~0` will be `111111111` in 1's complement and then `-(0000000+1) = -000000001` in [[Two's Complement]] which is -1
- So for any positive number, the answer will generally be negative.

## Binary **Shift** Operator
- **Left Shift (<<)** - Remember the sign as Left shift less than.
	- `7 << 2` This means move the binary positions of 7 to the left by two positions. 111 will become 111 00 which is 28.
	- *Formula* - `a << b = a * 2^b` 
		- 7<< 2 = 7 * 2^2 = 28
- **Right Shift (>>)** - Move to the right side you might drop the nums
	- `7 >> 2` = two 1's will get dropped and will become 00001 = 1
	- *Formula -* `a >> b = a // 2^b` 
		- 7 // 4 = 1


# Use of Bit Manipulation - in Problems
- **Bit Masking -** The number we use to access a specific bit in the byte of data is called the BitMask. In problems our main task will be to think of BitMask.
- Example - OddEven using Bit
	- We know any odd number has 1 at the last bit.
	- So we can do something to access the last bit only.
	- We apply the `&` operator with 1, and operator gives 1 only with 1, else 0. So all the number will either become 0 for even and 1 for odd.
```
- return num & 1 : 1 for odd, 0 means even
```

### Check Power of 2
[[Get Set Clear i-th Bit]]

### Clear last i bits of a number
```Pseudo
num = 15 and i = 2
15 = 1111
clear 2 bits = 1100 = 12
```
- Need a bitmask which will become 0.
	- `0 & 0 = 1 & 0 = 0`
	- So we need apply `&` with the last i-th bit having 0, every other bit needs to be 1.
	- If we choose a num having all 1 in it's bin and apply `num << i` that will make the last i bits 0
	- **The number having all digits 1 in its binary is`-1`**
## Count Set Bits
Number of 1's. - [LC]()
##### Strategy
- Found the last Bit. (We have seen how can we access the last digit in the power of 2).
	- `num & 1` will give the last digit.
		- 0 means last bit is 0.
		- Any other num will mean the last bit is 1
- Keep adding to the `Count` if the bit is non zero.
- And now we will want our num to get `shifted` to right and the last digit gets updated.
- We need to keep doing this till the time we reach the num as 0.