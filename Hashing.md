# Hash Maps

## Overview

- Operates in **O(1) time complexity** for retrieval.
- Directly locates values using a **key** rather than traversing the entire structure.

### Example

```java
map.get("Rahul");
```

Output: `90` in **O(1)** time.

---

## Understanding Hashing Concepts

### 1. Hashcode

- A method that generates a unique **integer hash code**.
- Facilitates **efficient storage and retrieval** of data.

#### Example

```java
String a = "Shiv";
int code = a.hashCode();
```

Output: A numerical representation (e.g., `12363`).

---

### 2. Hashing

- Converts a large hash code into a **fixed-size** value for better storage and retrieval efficiency.

#### Example

```java
hash % 10;
```

---

### 3. Collision - When Two Keys Have the Same Hash Code

#### Example

```
72346, 73786, 92366
```

Applying hashing:

```
Mod of all three is 0.
```

- This scenario is called a **collision**, where different keys yield the same hash value.

---

## Handling Collisions

### **Method 1: Chaining**

- Uses a **linked list** to store multiple values at the same index.
- Not ideal because it increases lookup time **from O(1) to O(n)** in the worst case.

#### **Solving Chaining with Simple Uniform Hashing**

Assumptions:

- Keys are **randomly and uniformly distributed**.
- The probability of each key hashing to any bucket is **equal**.

Expected time complexity: **O(1 + λ)**

λ is the Load Fact = ( n / m) - Expected Key per-slot 

---
# Rehashing in HashMaps

## **What is Rehashing?**
Rehashing is the process of **resizing and reorganizing a hashmap** when it becomes too full or inefficient due to excessive collisions.

## **Why Do We Need Rehashing?**
HashMaps are designed for **fast lookups (O(1) on average)**, but if too many elements are in the same bucket due to collisions, linked lists grow longer, making lookups **slower (O(n) in the worst case)**.

Rehashing helps by:
- **Increasing the size of the underlying array** (typically doubling it).
- **Recomputing hash values** for all existing keys based on the new array size.
- **Reinserting all elements into the new array** to distribute them more evenly.

## **When Does Rehashing Happen?**
Rehashing is typically triggered when the **load factor** exceeds a certain threshold.
- **Load factor** = `(number of elements) / (size of the array)`
- Java’s `HashMap` has a default **load factor of 0.75**, meaning rehashing happens when it's 75% full.

## **How Rehashing Works**
1. **Create a larger array** (usually **double the previous size**).
2. **Recompute hash indexes** for existing keys.
3. **Reinsert all key-value pairs** into the new array.

## **Example of Rehashing**
Let’s say we have a hashmap with an array of size `4`:
```
Index 0 → ("apple", 10)  
Index 1 → ("orange", 20)  
Index 2 → ("banana", 30)  
Index 3 → ("grape", 40)  
```
Now, if we insert another key (`"peach", 50`), the load factor exceeds **0.75**, so rehashing occurs:
1. The array size **doubles to 8**.
2. Each key is **rehashed** and placed in a new index.
3. The new hashmap might look like this:
   ```
   Index 0 → ("apple", 10)  
   Index 2 → ("banana", 30)  
   Index 4 → ("grape", 40)  
   Index 5 → ("peach", 50)  
   Index 7 → ("orange", 20)  
   ```

## **Downsides of Rehashing**
- **Expensive Operation**: Rehashing requires **O(n)** time because every key must be **rehashed and reinserted**.
- **Memory Overhead**: Temporarily, both the old and new arrays exist in memory.
- **May Cause Performance Spikes**: A single insertion might trigger a rehash, slowing that operation.

## **Key Takeaways**
- **Rehashing resizes the hashmap to maintain efficiency**.
- **It happens when the load factor exceeds a threshold (like 0.75 in Java’s HashMap)**.
- **Rehashing ensures better distribution and fewer collisions** but is computationally expensive.

---
Would you like to see an implementation of rehashing in Java or Python?
---






### **Hash Functions to Optimize Storage**

#### 1. **Division Method**

```java
h(k) = key % m;
```

- `m` should ideally be a **prime number** to reduce clustering.

#### 2. **Multiplication Method** (More efficient than division)

```java
h(k) = floor(m * (k * A % 1));
```

- `A` is a fractional constant (commonly `0.6138`) for **better key distribution**.

---

### **Method 2: Open Addressing (Handling Collisions Without Linked Lists)**

- **One item per slot**, searches for the **next available slot** when a collision occurs.

#### Example

1. `h(33) -> index 1`
2. If occupied, probe to **next available index**.

### **Types of Probing**

#### 1. **Linear Probing**

- Looks for the **next immediate empty slot**.
- **Issue**: Can cause clustering.

#### 2. **Double Hashing**

- Uses a **secondary hash function** to determine step size for probing.
- **Advantage**: Reduces clustering.

---

## **Using HashMaps in Java**

### **Syntax**

```java
HashMap<KeyType, ValueType> map = new HashMap<>();
```

#### Example

```java
HashMap<String, Integer> map = new HashMap<>();
```

### **Adding Values to a HashMap**

```java
map.put("India", 120);
```

### **Printing a HashMap**

```java
System.out.println(map);
```

- **Order is not guaranteed**; Java’s `HashMap` does not maintain insertion order.

#### Example

```java
map.put("India", 120);
map.put("China", 140);
map.put("US", 330);
```

- The printed order **may differ**.

### **Searching in a HashMap**

```java
map.get("India");
```

### **Useful HashMap Methods**

1. `map.getOrDefault("Key", DefaultValue);` → Returns the default value if the key is not found.
2. `map.containsKey("Key");` → Checks if a key exists.

---

## **Using Sets in Java**

- A `Set` is a collection that **does not allow duplicates**.

#### Example

```java
Set<Integer> set = new HashSet<>();
set.add(56);
set.add(56); // Only one instance is stored.
