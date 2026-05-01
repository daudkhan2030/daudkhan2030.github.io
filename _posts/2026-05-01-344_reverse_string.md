---
title: "🌸 LeetCode Problem 344: Reverse String — Index Swapping O(1) "
date: 2026-05-01
layout: single
categories:
  - engineering
---

🔍 **LeetCode Problem 344: Reverse String — Index Swapping**

এটা খুব ইজি । যাস্ট সোয়াপিং করলেই হচ্ছে । 

## 💡 Intuition (মেইন আইডিয়া)

প্রথমে `s` (character array/vector) এর size বের করি (ধরা যাক ৫, যেমন `"hello"` হলে)। তারপর দুইটা pointer নেই—
`l = 0` (শুরুর index) এবং `r = size - 1` (শেষের index)।

এরপর `while (l < r)` কন্ডিশনে লুপ চালাই। প্রতিবার:

* `s[l]` আর `s[r]` swap করি
* তারপর `l++` (বাম দিক থেকে এগোই)
* `r--` (ডান দিক থেকে পিছাই)

এভাবে দুই দিক থেকে ভিতরের দিকে আসতে আসতে পুরো string reverse হয়ে যায়।

অথবা একই জিনিস `for` loop দিয়েও করা যায়:
`for (l = 0, r = size - 1; l < r; l++, r--)` → ভিতরে শুধু `swap(s[l], s[r])`

## 🧠 কীভাবে কাজ করে?

এভাবে দুই দিক থেকে ভিতরের দিকে আসতে আসতে পুরো string reverse হয়ে যায়।

---

## ⚡ Code (C++)

```cpp
class Solution {
public:
    void reverseString(vector<char>& s) {
        int l = 0;
    int r = s.size() - 1;

    while (l < r)
      swap(s[l++], s[r--]);
    }
};
```

---


#LeetCode #DSA #Cpp #ProblemSolving
