---
title: "Bitwise Operators and Usages with Mnemonics"
date: 2026-04-01
layout: single
categories:
  - engineering
---

💡

- `&` → **“both 1 হলে 1              ( 1 এর ক্ষেত্রে বা শুধু  common bits রাখে)”**
- `|` → **“যেকোনো একটাও 1 হলে 1  (bit ON করে)”**
- `^` → **“different হলে 1           (toggle checker)”**
- `~` → **“সব bit উল্টে দেয়          (0↔1 flip)”**
- `<<` → **“left shift = ×2ⁿ          (bit বামে সরায়)”**
- `>>` → **“right shift = ÷2ⁿ         (bit ডানে সরায়)”**


- `&` এর ইউসেজ :  Odd, Even ডিটারমাইন এর জন্য & 1 দিয়েই করা যায় । 
    
    if ((n & 1) == 0)
        return true;
    else
        return false;

Cause, 
44 ->          

<pre>
   1 0 1 1 0 0
&  0 0 0 0 0 1
   ------------
   0 0 0 0 0 0
</pre>

আর এই পদ্ধতি রেগুলার % বা মড এর থেকেও ফাস্ট কারণ এখানে সিপিউ কে শুধু বিট চেঞ্জ করলেই হয় যেখানে % এ ভাগ করে ভাগফল দেখা লাগে । 

- `^` এর ইউসেজ :  👇 নাম্বার সোয়াপিং (Number Swapping) সম্ভব শুধুমাত্র ৩ টা Instructions এ । এটা 🧠 🔥 XOR-এর core property
x ^ y ^ y = x মানে: একটা value কে আরেকটা value দিয়ে XOR করলে, পরে আবার সেই same value দিয়ে XOR করলে আগেরটা ফিরে আসে

<pre>
a = a ^ b;      
b = a ^ b;
a = a ^ b;
</pre>

</pre>
a = 5 → 101  ,  b = 3 → 011

 1.  a       1 0 1
   ^ b;    ^ 0 1 1
           = 1 1 0 (6)

 2.  a       1 1 0
   ^ b;    ^ 0 1 1
           = 1 0 1 (5)

 3.  a       1 1 0
   ^ b;    ^ 1 0 1
           = 0 1 1 (3)

👉 তুমি ভাবতে পারো:

a = a ^ b   → a now holds "combined info"

👉 তারপর:

b = a ^ b   → b থেকে b remove → a পাওয়া যায়
a = a ^ b   → a থেকে a remove → b পাওয়া যায়

🧠 super short summary
- same value দিয়ে twice XOR করলে original ফিরে আসে

a = a ^ b
b = a ^ b → gets a
a = a ^ b → gets b
 </pre>
