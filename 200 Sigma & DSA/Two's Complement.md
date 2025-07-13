**Two’s complement** is a mathematical method and a binary encoding scheme used to represent both positive and negative integers in binary form. It is the most common way computers store signed integers.

## Why Use Two’s Complement?

- **Simplicity:** Arithmetic operations (addition, subtraction) are easy and efficient.
    
- **Single Zero:** Only one representation for zero (unlike some other systems).
    
- **Easy Negation:** Negating a number is straightforward.

## How Does Two’s Complement Work?

Let’s see how to represent a negative number (e.g., -5) in 8-bit binary:

1. **Write the positive number in binary:**  
    5 in 8 bits: `00000101`
    
2. **Invert all the bits (one’s complement):**  
    `11111010`
    
3. **Add 1 to the result:**  
    `11111010` + `1` = `11111011`

So, **-5** in 8-bit two’s complement is:  
`11111011`
## Example Table (8 bits)

|Decimal|Binary (Two’s Complement)|
|---|---|
|5|00000101|
|-5|11111011|
|-1|11111111|
|0|00000000|

## How to Find Two’s Complement

For any N-bit number:

1. **Write the number in binary.**
    
2. **Invert all bits** (change 0 to 1, and 1 to 0).
    
3. **Add 1** to the result.

```Python
def print_twos_complement(n, bits):
	print(format(n & (2**bits - 1), f'0{bits}b'))

  

print_twos_complement(-1, 8) # 8 bits: 11111111

print_twos_complement(-1, 16) # 16 bits: 1111111111111111
```

#### Explanation
```python

n = -1 bits = 8 print(format(n & (2**bits - 1), f'0{bits}b'))
```

###### Bit Masking: `n & (2**bits - 1)`

- `2**bits` calculates 2 to the power of the number of bits. For 8 bits, `2**8 = 256`.
- `2**bits - 1` gives you a mask where all bits are 1. For 8 bits: `256 - 1 = 255`, which in binary is `11111111`.
    
- `n & (2**bits - 1)`  
    This performs a bitwise AND between `n` and the mask.
    
    - For `n = -1`, in Python, negative numbers are stored with an infinite number of leading 1s (in two’s complement).
        
    - The mask (`11111111`) keeps only the lowest 8 bits of `n`.
        
    - So, `-1 & 0xFF` (where `0xFF` is 255 in hex) results in `11111111` (8 bits).

###### 3. Formatting: `format(..., f'0{bits}b')`

- `format(value, '08b')`
    
    - `'08b'` means:
        
        - `0` → pad with zeros
            
        - `8` → total width is 8 digits
            
        - `b` → binary format
            
- This ensures the output is always 8 bits wide, padded with zeros if needed.
##### Summary Table

|Code Part|What it does|
|---|---|
|`n & (2**bits - 1)`|Gets the lowest `bits` bits of `n`|
|`format(..., f'0{bits}b')`|Formats as zero-padded binary string|
|`print(...)`|Prints the result|

**In short:**  
The code takes a negative number, keeps only the desired number of bits (emulating two’s complement), and prints it as a binary string.

Let me know if you want to see how it works for other numbers or bit widths!
## Why is it Useful?

- **Arithmetic is the same:** Adding negative and positive numbers works without special rules.
    
- **Efficient hardware:** Circuits are simpler and faster.
    

## Quick Facts

- The leftmost bit (most significant bit) indicates the sign:  
    `0` = positive, `1` = negative.
    
- The range for N bits:  
    `-(2^(N-1))` to `(2^(N-1) - 1)`  
    (e.g., for 8 bits: -128 to 127)
    

**In summary:**  
Two’s complement is a clever way for computers to handle negative numbers, making binary arithmetic simple and efficient!

Let me know if you want to see more examples or a visualization!