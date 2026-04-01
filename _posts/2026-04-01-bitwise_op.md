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

Odd, Even ডিটারমাইন এর জন্য & 1 দিয়েই করা যায় । 
    
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
