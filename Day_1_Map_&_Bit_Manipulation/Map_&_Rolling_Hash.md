# 🔹 PLACEMENT QUICK REVISION – MAP & ROLLING HASH

---

## 🔹 MAP – Core Facts (Must Know)

- Stores **key–value pairs**
- **Keys are unique**, values can repeat
- Lookup by key is very fast
- `Map` is an **interface** → cannot instantiate directly

✔ Correct:

Map<Integer, String> map = new HashMap<>();

---

## 🔹 Types of Maps (Most Asked)
### HashMap

- No order
- Fastest
- Allows 1 null key, many null values
- Avg time: O(1)

### LinkedHashMap

- Maintains insertion order
- Slightly slower than HashMap
- Allows null key & values
- Avg time: O(1)

### TreeMap

- Stores keys in sorted order
- Uses Red-Black Tree
- ❌ No null keys
- Time: O(log n)

### ConcurrentHashMap

- Thread-safe, high performance
- ❌ No null key / values

# Preferred over Hashtable

## 🔹 Collision Handling (Very Important)

- Hash function → key to index
- Same index for 2 keys → collision
### Java handles by:

- Linked List (old)
- Balanced Tree (Java 8+) if chain becomes long
- Worst case becomes O(log n) instead of O(n)

## 🔹 Load Factor & Rehashing

- Default load factor = 0.75

When:

- size > capacity × loadFactor


## → Rehashing happens (table resizes)

- ⚠ Rehashing is costly
- ✔ But average complexity still O(1) (amortized)

## 🔹 Null Handling (Very Common MCQ)
| Map  | Type	| Null Key | Null Values
HashMap	| ✔ | (one) | 	✔
LinkedHashMap | 	✔ | 	✔ | 
TreeMap	 | ❌ | 	✔ |   |
Hashtable	| ❌	| ❌ |  |
## 🔹 ROLLING HASH (Rabin–Karp) – Placement Level
### 🔹 Why used?

- Fast substring search

- Avoids repeated string comparison

Used in:

- Pattern matching

- Plagiarism detection

- Substring equality

### 🔹 Core Idea

Instead of comparing strings:

- Convert strings → hash values

- Compare hashes first

- If hashes match → then compare characters (to avoid collision)

## 🔹 Time Complexity

- Best / Average: O(n + m)

- Worst (many collisions): O(n × m)

## 🔹 Rolling Hash Formula (Remember This)

Hash:

H = (s[0]*d^(m-1) + ... + s[m-1]) % q


Rolling update:

newHash = (d * (oldHash - firstChar * h) + nextChar) % q


Where:

d = base (usually 256)

q = large prime

h = d^(m-1) % q

🔹 Collision Handling (Critical Line)

⚠ Different strings can have same hash

So ALWAYS:

When hash matches → verify characters manually

Use:

Large prime q

Good base d

## 🔹 Normal Hash vs Rolling Hash
Normal Hash	Rolling Hash
Recompute full	Update in O(1)
Slow for windows	Fast sliding
Not reusable	Reusable
## 🔹 5 Interview One-Liners (Memorize These)

HashMap average complexity = O(1), worst = O(n)

TreeMap is implemented using Red-Black Tree

Default load factor of HashMap = 0.75

Java 8 converts long collision chains into balanced trees

Rabin–Karp works in O(n + m) using rolling hash
