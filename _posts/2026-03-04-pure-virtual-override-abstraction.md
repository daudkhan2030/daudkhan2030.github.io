---
title: "About Virtual Function - Pure Virtual Function - Override - Abstraction"
date: 2026-03-04
layout: single
categories: 
  - engineering
tags:
  - distributed-systems
  - caching
  - architecture
---

# Things to know about Virtual Function - Pure Virtual Function - Override - Abstraction

🎐🎐🎐🎐🎐🎐🎐🎐🎐🎐 🎐🎐🎐🎐🎐🎐🎐🎐🎐🎐 🎐🎐🎐🎐🎐🎐🎐🎐🎐🎐 🎐🎐🎐🎐🎐🎐

| জিনিস | মানে |
| --- | --- |
| pure virtual | করতেই হবে, আলাদা হবেই |
| virtual | ডিফল্ট আছে, চাইলে বদলাবে |
| base class | rule বানায় |
| child class | কাজ করে |

এক লাইনের golden rule (RTOS-এ মনে রাখবে)

> 🔸 যেটা ছাড়া system চলে না → pure virtual
> 
> 
> 🔸 **যেটা সবার জন্য একই → virtual**
> 

### Virtual Function- Pure Virtual - Override এসব মাল সামানা কেন লাগে ?

```cpp
Scheduler
   |
   |-- Task* ----> SensorTask::run()
   |
   |-- Task* ----> CommTask::run()
   |
   |-- Task* ----> LoggerTask::run()
```

## Diagram-এর আসল মানে কী

এই diagram বলে:

👉 **Scheduler শুধু `Task*` জানে**

👉 **Scheduler শুধু একটা common function ডাকতে চায়**

## তাহলে virtual / pure virtual কেন?

কারণ:

- Scheduler জানে না এটা কোন task
- Scheduler শুধু base pointer ব্যবহার করে
- কিন্তু ভিতরের কাজ child অনুযায়ী আলাদা
- এটা শুধু scheduler-friendly design, যাতে একই call দিয়ে আলাদা কাজ চালানো যায়।

এই situation-এ:

👉 **virtual / pure virtual দরকার**

## Golden rule মনে রাখো

> 🔹 Common caller + different behavior → virtual / pure virtual
> 
> 
> 🔹 **Direct call + known type → normal function**
>
