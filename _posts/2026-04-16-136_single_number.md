---
title: "🌸 LeetCode Problem 136: Single Number — XOR দিয়ে Efficient Solution"
date: 2026-04-16
layout: single
categories:
  - engineering
---

🔍 **LeetCode Problem: Single Number — XOR দিয়ে Efficient Solution**

আজ আমি একটা classic problem solve করেছি:
👉 এমন একটা array দেওয়া থাকে যেখানে সব number দুবার করে আছে, শুধু একটা number একবার আছে — সেটাই বের করতে হবে।

---

## 💡 Intuition (মেইন আইডিয়া)

এখানে আমি use করেছি **XOR (^) bitwise operator**।

👉 XOR-এর কিছু powerful property আছে:

* `a ^ a = 0` (একই number cancel হয়ে যায়)
* `a ^ 0 = a`
* XOR commutative & associative → order matter করে না

---

## 🧠 কীভাবে কাজ করে?

ধরো array:
`[3, 2, 2, 4, 4]`

Step by step XOR করলে:

* 3 ^ 2 ^ 2 ^ 4 ^ 4
  = 3 ^ (2 ^ 2) ^ (4 ^ 4)
  = 3 ^ 0 ^ 0
  = **3**

👉 অর্থাৎ সব duplicate number নিজে নিজে cancel হয়ে যায়
👉 শেষে শুধু unique number থাকে

---

## ⚡ Code (C++)

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int a = 0;
        for (int x : nums) {
            a ^= x;
        }
        return a;
    }
};
```

---

## 🚀 কেন এই approach best?

* ⏱️ Time Complexity: **O(n)** (একবারই traverse)
* 🧠 Space Complexity: **O(1)** (extra memory লাগে না)
* ⚡ খুব clean & elegant solution

---

## 🎯 Final Takeaway

👉 XOR হচ্ছে এই problem-এর জন্য perfect tool
👉 duplicate elements নিজে নিজেই eliminate হয়ে যায়
👉 efficient + interview-friendly approach

---

1️⃣ 3 2 2 4 4
a = 0 0 0
```
a = (0) 0 0 0 ^ (3) 0 1 1 = 0 1 1   (3) 
a = (3) 0 1 1 ^ (2) 0 1 0 = 0 0 1   (1) 
a = (1) 0 0 1 ^ (2) 0 1 0 = 0 1 1   (3) 
a = (3) 0 1 1 ^ (4) 1 0 0 = 1 1 1   (7) 
a = (7) 1 1 1 ^ (4) 1 0 0 = 0 1 1   (3)
```
2️⃣ 2 2 3 4 4
a = 0 0 0
```
a = (0) 0 0 0 ^ (2) 0 1 0 = 0 1 0   (2) 
a = (2) 0 1 0 ^ (2) 0 1 0 = 0 0 0   (0) 
a = (0) 0 0 0 ^ (3) 0 1 1 = 0 1 1   (3) 
a = (3) 0 1 1 ^ (4) 1 0 0 = 1 1 1   (7) 
a = (7) 1 1 1 ^ (4) 1 0 0 = 0 1 1   (3)
```
3️⃣ 2 2 4 4 3
a = 0 0 0
```
a = (0) 0 0 0 ^ (2) 0 1 0 = 0 1 0   (2) 
a = (2) 0 1 0 ^ (2) 0 1 0 = 0 0 0   (0) 
a = (0) 0 0 0 ^ (4) 1 0 0 = 1 0 0   (4) 
a = (4) 1 0 0 ^ (4) 1 0 0 = 0 0 0   (0) 
a = (0) 0 0 0 ^ (3) 0 1 1 = 0 1 1   (3)
```
4️⃣ 2 3 2 4 4
a = 0 0 0
```
a = (0) 0 0 0 ^ (2) 0 1 0 = 0 1 0   (2) 
a = (2) 0 1 0 ^ (3) 0 1 1 = 0 0 1   (1) 
a = (1) 0 0 1 ^ (2) 0 1 0 = 0 1 1   (3) 
a = (3) 0 1 1 ^ (4) 1 0 0 = 1 1 1   (7) 
a = (7) 1 1 1 ^ (4) 1 0 0 = 0 1 1   (3)
```
5️⃣ 2 2 4 3 4
a = 0 0 0
```
a = (0) 0 0 0 ^ (2) 0 1 0 = 0 1 0   (2) 
a = (2) 0 1 0 ^ (2) 0 1 0 = 0 0 0   (0) 
a = (0) 0 0 0 ^ (4) 1 0 0 = 1 0 0   (4) 
a = (4) 1 0 0 ^ (3) 0 1 1 = 1 1 1   (7) 
a = (7) 1 1 1 ^ (4) 1 0 0 = 0 1 1   (3)
```
🔚 একদম final intuition

👉 যেখানেই দেখো:

(2) 0 1 0 ^ (2) 0 1 0 = 0 0 0  
(4) 1 0 0 ^ (4) 1 0 0 = 0 0 0  

👉 শেষে শুধু থাকে:

(3) 0 1 1

#LeetCode #DSA #BitManipulation #XOR #Cpp #ProblemSolving
