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
