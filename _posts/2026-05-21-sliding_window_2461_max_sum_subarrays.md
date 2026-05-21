---
title: 🌸 LeetCode 2461 — Sliding Window, Frequency Map & Distinct Count"
date: 2026-05-21
layout: single
categories:
  - engineering
---

# 🌸 Sliding Window Pattern বুঝার একটা সুন্দর Example

আজ `2461. Maximum Sum of Distinct Subarrays With Length K` problem করতে গিয়ে Sliding Window pattern নিয়ে কিছু interesting বিষয় বুঝলাম।

এই problem এর মূল focus আসলে:
- Fixed-size Sliding Window
- Frequency Counting
- Distinct Element Tracking
- Window Enter / Exit Operations

---

# 🌸 `k` Variable নিয়ে Understanding

প্রথমে confusing লাগছিল `k` constant নাকি dynamic।

আসলে:

maximumSubarraySum(vector<int>& nums, int k)

এখানে k হচ্ছে input parameter।

মানে:

- User / Problem setter k পাঠাবে
- পুরো execution এ k same থাকবে
- Window size fixed থাকবে

অর্থাৎ এটা classic Fixed-size Sliding Window problem।

🌸 Frequency Map Understanding

এই line:

unordered_map<int, int> count;

এখানে:

key   -> number
value -> frequency

যেমন:

nums = {1,2,5,4}

তাহলে internally:

{
 1:1,
 2:1,
 5:1,
 4:1
}

store হতে পারে।

এটা পুরো array এর frequency না।

বরং:

Current sliding window এর frequency।

🌸 Interesting Part — ++count[nums[i]]

এই line অনেক important:

if (++count[nums[i]] == 1)

এখানে কয়েকটা operation হয়:

```
count[nums[i]] access হয়
Key না থাকলে default value 0 create হয়
Frequency increment হয়
Incremented value 1 কিনা check হয়
```

যদি 1 হয়:

- বুঝতে হবে number first time window তে এসেছে
- তাই distinct++

🌸 Distinct Count কেন দরকার?
if (distinct == k)

মানে:

Window size = k
Distinct elements = k

অর্থাৎ:

- সব elements unique।
- এটাই problem এর main condition।

🌸 Sliding Window এর Real Beauty

Naive solution এ:  প্রতিবার নতুন subarray calculate করতে হতো

কিন্তু Sliding Window এ:

- new element add
- old element remove
- sum update
- frequency update

সব O(1) average time এ হচ্ছে।

তাই পুরো solution:  O(n)

🌸 Optimal Sliding Window Solution (C++)

```cpp
class Solution {
 public:
  long long maximumSubarraySum(vector<int>& nums, int k) {
    long ans = 0;
    long sum = 0;
    int distinct = 0;

    unordered_map<int, int> count;

    for (int i = 0; i < nums.size(); ++i) {

      sum += nums[i];

      if (++count[nums[i]] == 1)
        ++distinct;

      if (i >= k) {

        if (--count[nums[i - k]] == 0)
          --distinct;

        sum -= nums[i - k];
      }

      if (i >= k - 1 && distinct == k)
        ans = max(ans, sum);
    }

    return ans;
  }
};
```

🌸 Personal Note --> এই problem করতে গিয়ে আবার বুঝলাম:

- Interview এ অনেক সময় syntax এর চেয়ে বেশি important হচ্ছে pattern recognition।

কারণ:
```
Sliding Window identify করা
Frequency map বুঝা
Window enter/exit logic বুঝা
```
এগুলোই মূল skill।
