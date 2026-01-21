# Bit Manipulation — Striver Course Revision Notes (Placement Oriented)

---

# 🔹 INTRODUCTION TO BIT MANIPULATION

## What is Bit Manipulation?

Bit manipulation deals with directly working on the **binary representation of numbers** using bitwise operators.

Why important:
- Very fast operations (`O(1)`)
- Used in:
  - Optimization problems  
  - Subsets / Masks  
  - DP with Bitmask  
  - Competitive programming  
  - Interview tricks  

---

## Binary Representation

- Every integer is stored in **binary (base-2)**
- Example:
5 = 101
6 = 110
7 = 111


---

# 🔹 BITWISE OPERATORS

| Operator | Symbol | Meaning |
|----------|--------|---------|
| AND      | `&`    | Both bits must be 1 |
| OR       | `|`    | At least one bit is 1 |
| XOR      | `^`    | Bits must be different |
| NOT      | `~`    | Inverts all bits |
| Left Shift  | `<<` | Multiply by 2 |
| Right Shift | `>>` | Divide by 2 |

Examples:
5 & 3 → 101 & 011 = 001 = 1
5 | 3 → 101 | 011 = 111 = 7
5 ^ 3 → 101 ^ 011 = 110 = 6


---

# 🔹 IMPORTANT CONCEPTS & TRICKS

---

## Check Even or Odd

```java
if ((n & 1) == 0) → Even  
else → Odd
```
## Check if ith Bit is Set
if ((n & (1 << i)) != 0)  
    bit is set
Set the ith Bit
n = n | (1 << i);

Clear (Unset) the ith Bit
n = n & ~(1 << i);

Toggle the ith Bit
n = n ^ (1 << i);

Remove the Rightmost Set Bit

Very important trick:

n = n & (n - 1);


Removes the lowest set bit.

Get the Rightmost Set Bit
int rmsb = n & (-n);


Gives value of the lowest set bit.

Check if Number is Power of Two
if (n > 0 && (n & (n - 1)) == 0)
    → Power of Two

Count Number of Set Bits (Brian Kernighan Algorithm)
int count = 0;
while (n > 0) {
    n = n & (n - 1);
    count++;
}


Time Complexity → O(number of set bits)

Swap Two Numbers without Extra Variable
a = a ^ b;
b = a ^ b;
a = a ^ b;

🔹 XOR TRICKS (VERY IMPORTANT)
Properties of XOR

a ^ a = 0

a ^ 0 = a

XOR is commutative & associative

Find the Number Occurring Once (Others Twice)
int ans = 0;
for (int x : arr)
    ans ^= x;


Because duplicates cancel out.

Find Two Numbers Occurring Once (Others Twice)

Steps:

XOR all elements → xor = a ^ b

Find rightmost set bit → bit = xor & (-xor)

Divide numbers into two groups using this bit

XOR each group separately

🔹 LEFT SHIFT & RIGHT SHIFT
Left Shift <<

Multiplies number by 2

n << 1 = n * 2  
n << k = n * (2^k)

Right Shift >>

Divides number by 2

n >> 1 = n / 2  
n >> k = n / (2^k)

🔹 SUBSETS USING BIT MASKING

Used to generate all subsets of a set

For a set of size n:

Total subsets = 2^n

Loop from 0 to (1<<n) - 1

Example:

for (int mask = 0; mask < (1 << n); mask++) {
    for (int i = 0; i < n; i++) {
        if ((mask & (1 << i)) != 0) {
            // include element i
        }
    }
}

🔹 BIT MASKING CONCEPT

Used to:

Represent subsets

Track visited states

DP with bitmask

Example:

Mask = 1011
→ elements at positions 0,1,3 are selected

🔹 IMPORTANT INTERVIEW PROBLEMS (FROM STRIVER)
1️⃣ Check if ith Bit is Set
2️⃣ Set / Clear / Toggle ith Bit
3️⃣ Count Set Bits
4️⃣ Power of Two
5️⃣ Single Number (XOR)
6️⃣ Two Unique Numbers
7️⃣ Generate Subsets
8️⃣ Minimum Bit Flips to Convert A → B
Minimum Bit Flips to Convert A to B
int x = a ^ b;
count set bits in x

🔹 TIME COMPLEXITIES
Operation	Complexity
Check / Set / Clear bit	O(1)
Count set bits (normal)	O(32)
Brian Kernighan algorithm	O(no. of set bits)
Subset generation	O(n * 2^n)
🔹 COMMON MISTAKES (INTERVIEW WARNINGS)

Forgetting parentheses in shifts:
❌ n & 1 << i
✔ (n & (1 << i))

Using signed right shift wrongly

Not handling negative numbers carefully

Forgetting to check n > 0 in power of two

🔹 WHY BIT MANIPULATION IS IMPORTANT

Faster than normal arithmetic

Used in:

Competitive programming

DP with bitmask

Graph problems

Optimization tricks

✅ END OF BIT MANIPULATION NOTES
