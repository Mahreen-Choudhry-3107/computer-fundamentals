# Number Systems & Data Representation

> Deep dive into how computers represent numbers, characters, and perform bitwise operations.

---

## 1. Why Number Systems Matter

Computers store and process everything as **binary (0s and 1s)** at the hardware level. Understanding number systems helps with:
- Low-level programming (bit manipulation, embedded systems)
- Debugging memory dumps, hex addresses
- Competitive programming (bitwise tricks)
- Networking (IP addresses, subnet masks)
- Cryptography and hashing

---

## 2. Types of Number Systems

| System | Base | Digits |
|---|---|---|
| Binary | 2 | 0, 1 |
| Octal | 8 | 0–7 |
| Decimal | 10 | 0–9 |
| Hexadecimal | 16 | 0–9, A(10)–F(15) |

---

## 3. Conversions

### 3.1 Decimal → Binary
Repeatedly divide by 2, collect remainders bottom-up.

```
45 ÷ 2 = 22 remainder 1
22 ÷ 2 = 11 remainder 0
11 ÷ 2 = 5  remainder 1
5  ÷ 2 = 2  remainder 1
2  ÷ 2 = 1  remainder 0
1  ÷ 2 = 0  remainder 1

Reading remainders bottom-up: 101101
So, 45 (decimal) = 101101 (binary)
```

### 3.2 Binary → Decimal
Multiply each bit by 2^(position from right, starting at 0).

```
101101 = 1×2⁵ + 0×2⁴ + 1×2³ + 1×2² + 0×2¹ + 1×2⁰
       = 32 + 0 + 8 + 4 + 0 + 1
       = 45
```

### 3.3 Decimal → Hexadecimal
Repeatedly divide by 16.

```
255 ÷ 16 = 15 remainder 15 (F)
15  ÷ 16 = 0  remainder 15 (F)

255 (decimal) = FF (hex)
```

### 3.4 Binary → Hexadecimal (shortcut)
Group binary digits into sets of 4 (from right), convert each group.

```
1010 1101  →  A D  →  AD (hex)
```

### 3.5 Binary → Octal (shortcut)
Group binary digits into sets of 3 (from right).

```
101 101  →  5 5  →  55 (octal)
```

---

## 4. Data Units

```
1 Bit       = 0 or 1
1 Nibble    = 4 bits
1 Byte      = 8 bits
1 KB        = 1024 Bytes
1 MB        = 1024 KB
1 GB        = 1024 MB
1 TB        = 1024 GB
```

---

## 5. Signed vs Unsigned Numbers

- **Unsigned** – only positive values (0 to 2ⁿ - 1)
- **Signed** – can represent negative values using **Two's Complement**

### Two's Complement (for negative numbers)
Steps to represent `-5` in 8-bit:
1. Write `5` in binary: `00000101`
2. Invert all bits (One's Complement): `11111010`
3. Add 1: `11111011` → this represents `-5`

**Why Two's Complement?**
- Only one representation for zero
- Addition/subtraction work using normal binary addition rules
- Simplifies CPU circuit design

---

## 6. Floating Point Representation (IEEE 754)

Used to represent decimal (real) numbers in binary.

```
[ Sign (1 bit) | Exponent (8 bits) | Mantissa (23 bits) ]   → 32-bit float
```

- **Sign bit** – 0 = positive, 1 = negative
- **Exponent** – scales the number (stored with a bias)
- **Mantissa** – the significant digits of the number

**Why it matters:** Explains floating-point precision errors, e.g., why `0.1 + 0.2 !== 0.3` in most programming languages.

---

## 7. Bitwise Operators

| Operator | Symbol | Description |
|---|---|---|
| AND | `&` | 1 only if both bits are 1 |
| OR | `\|` | 1 if at least one bit is 1 |
| XOR | `^` | 1 if bits are different |
| NOT | `~` | Inverts all bits |
| Left Shift | `<<` | Shifts bits left, multiplies by 2 per shift |
| Right Shift | `>>` | Shifts bits right, divides by 2 per shift |

### Examples
```
5  = 0101
3  = 0011

5 & 3 = 0001 = 1
5 | 3 = 0111 = 7
5 ^ 3 = 0110 = 6
~5    = ...11111010 (depends on bit width)
5 << 1 = 1010 = 10
5 >> 1 = 0010 = 2
```

### Common Bit Tricks (used in interviews)
```
Check if a number is even:      n & 1 == 0
Multiply by 2:                  n << 1
Divide by 2:                    n >> 1
Check if a number is power of 2: n & (n - 1) == 0
Swap two numbers without temp:  a ^= b; b ^= a; a ^= b;
Get the i-th bit:               (n >> i) & 1
Set the i-th bit:               n | (1 << i)
Clear the i-th bit:             n & ~(1 << i)
```

---

## 8. Character Encoding

| Encoding | Description |
|---|---|
| **ASCII** | 7-bit, 128 characters (English alphabet, digits, symbols) |
| **Extended ASCII** | 8-bit, 256 characters |
| **Unicode** | Universal standard supporting all world languages |
| **UTF-8** | Variable-length encoding (1–4 bytes), backward compatible with ASCII |
| **UTF-16** | Uses 2 or 4 bytes per character |

**Example:** Character `'A'` = ASCII value `65` = Binary `01000001`

---

## 9. Quick Revision Summary

- Binary is the native language of computers (2 states: ON/OFF)
- Conversions: Decimal ↔ Binary ↔ Octal ↔ Hex
- Two's Complement is the standard for representing negative integers
- IEEE 754 defines how decimals are stored (and explains float precision bugs)
- Bitwise operators are heavily used in optimization & competitive programming

---

## 10. Interview-Style Questions

1. Convert `-12` to its 8-bit Two's Complement form.
2. Why does `0.1 + 0.2` not equal `0.3` exactly in most languages?
3. Write a bitwise trick to check if a number is a power of 2.
4. What's the difference between ASCII and Unicode?
5. Convert `2F` (hex) to binary and decimal.
6. How would you swap two variables without using a temporary variable?

---

**Previous file ←** `introduction.md`
**Next file →** `operating-systems.md`
