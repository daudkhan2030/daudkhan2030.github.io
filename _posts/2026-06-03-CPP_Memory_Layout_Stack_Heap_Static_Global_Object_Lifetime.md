---
title: "🌸 C++ Memory Layout: Stack, Heap, Static, Global এবং Object Lifetime"
date: 2026-06-03
layout: single
categories:
    - notes
---
# C++ Memory Layout: Stack, Heap, Static, Global এবং Object Lifetime

## Introduction

C++-এ classes, objects, pointers, references, design patterns কিংবা large-scale systems নিয়ে কাজ করতে গেলে memory layout সম্পর্কে পরিষ্কার ধারণা থাকা প্রয়োজন।

অনেক সময় আমরা object create করি, function call করি, pointer pass করি, `new` ব্যবহার করি, singleton তৈরি করি—কিন্তু object আসলে কোথায় তৈরি হচ্ছে, কখন destroy হচ্ছে এবং memory কে manage করছে তা পরিষ্কার থাকে না।

এই post-এ C++-এর memory model-এর fundamental বিষয়গুলো আলোচনা করা হলো।

---

# একটি Program-এর Memory Layout

একটি সাধারণ C++ program-এর memory সাধারণত কয়েকটি অংশে বিভক্ত থাকে:

```text
+------------------+
|      Stack       |
+------------------+

+------------------+
|       Heap       |
+------------------+

+------------------+
| Static / Global  |
+------------------+

+------------------+
|   Code Segment   |
+------------------+
```

প্রতিটি অংশের দায়িত্ব আলাদা।

---

# Code Segment

এখানে executable instructions থাকে।

উদাহরণ:

```cpp
void Print()
{
    cout << "Hello";
}
```

`Print()` function-এর machine instructions code segment-এ সংরক্ষিত হয়।

সাধারণত program চলাকালীন এটি পরিবর্তন হয় না।

---

# Global Memory

Global variables program শুরু হওয়ার সময় create হয় এবং program শেষ হওয়ার সময় destroy হয়।

```cpp
int g_count = 0;
```

```text
Program Start
    ↓
g_count Created
    ↓
Program Running
    ↓
Program Exit
    ↓
g_count Destroyed
```

---

# Static Variables

Static variable-এর lifetime পুরো program জুড়ে থাকে।

```cpp
void Foo()
{
    static int count = 0;
}
```

এখানে:

```cpp
count
```

প্রথমবার create হবে।

পরবর্তীতে function call হলেও নতুন করে create হবে না।

---

উদাহরণ:

```cpp
void Foo()
{
    static int count = 0;

    count++;

    cout << count << endl;
}
```

Calls:

```cpp
Foo();
Foo();
Foo();
```

Output:

```text
1
2
3
```

কারণ static variable destroy হয়নি।

---

# Stack Memory

সবচেয়ে বেশি ব্যবহৃত memory area।

---

উদাহরণ:

```cpp
int a = 10;
```

অথবা

```cpp
Dog dog;
```

এগুলো stack-এ create হয়।

---

Function call হলে stack frame তৈরি হয়।

```cpp
void Foo()
{
    int x = 10;
}
```

Execution:

```text
Call Foo()
    ↓
Create Stack Frame
    ↓
Create x
    ↓
Function Ends
    ↓
Destroy x
    ↓
Remove Stack Frame
```

---

# Stack-এর সবচেয়ে গুরুত্বপূর্ণ বৈশিষ্ট্য

Automatic lifetime management।

```cpp
void Foo()
{
    Dog d;
}
```

Function শেষ হলে:

```cpp
d
```

automatic destroy হবে।

Programmer-এর কিছু করতে হবে না।

---

# Stack Object

```cpp
class Dog
{
public:
    Dog()
    {
        cout << "Created\n";
    }

    ~Dog()
    {
        cout << "Destroyed\n";
    }
};
```

```cpp
void Foo()
{
    Dog d;
}
```

Output:

```text
Created
Destroyed
```

---

# Heap Memory

Runtime-এ manually memory allocate করার জন্য heap ব্যবহার করা হয়।

---

উদাহরণ:

```cpp
int* p = new int(10);
```

Memory:

```text
Stack
-----
p

Heap
----
10
```

---

এখানে:

```cpp
p
```

stack-এ।

কিন্তু:

```cpp
new int(10)
```

heap-এ।

---

# Heap Object

```cpp
Dog* dog = new Dog();
```

Memory:

```text
Stack
-----
dog

Heap
----
Dog Object
```

---

# Delete

Heap memory programmer-কে release করতে হয়।

```cpp
delete dog;
```

---

যদি delete না করা হয়:

```cpp
Dog* dog = new Dog();
```

তাহলে memory leak হতে পারে।

---

# Memory Leak

```cpp
void Foo()
{
    Dog* dog = new Dog();
}
```

Function শেষ হলেও:

```cpp
Dog Object
```

heap-এ রয়ে যাবে।

কারণ:

```cpp
delete dog;
```

ডাকা হয়নি।

---

# Stack vs Heap

| Feature           | Stack       | Heap         |
| ----------------- | ----------- | ------------ |
| Allocation        | Automatic   | Manual       |
| Speed             | Fast        | Slower       |
| Lifetime          | Scope Based | Until Delete |
| Memory Management | Compiler    | Programmer   |
| Leak Risk         | No          | Yes          |

---

# Object Lifetime

Lifetime মানে object কতক্ষণ বেঁচে থাকবে।

---

## Stack Object

```cpp
void Foo()
{
    Dog d;
}
```

Lifetime:

```text
Function Entry
    ↓
Object Created
    ↓
Function Exit
    ↓
Object Destroyed
```

---

## Heap Object

```cpp
Dog* d = new Dog();
```

Lifetime:

```text
new
 ↓
Object Exists
 ↓
Object Exists
 ↓
Object Exists
 ↓
delete
 ↓
Destroyed
```

---

# Constructor এবং Destructor

Object create হলে constructor call হয়।

```cpp
Dog d;
```

Calls:

```cpp
Dog()
```

---

Object destroy হলে destructor call হয়।

```cpp
~Dog()
```

---

Example:

```cpp
class Dog
{
public:
    Dog()
    {
        cout << "Create\n";
    }

    ~Dog()
    {
        cout << "Destroy\n";
    }
};
```

Output:

```text
Create
Destroy
```

---

# RAII (Resource Acquisition Is Initialization)

Modern C++-এর সবচেয়ে গুরুত্বপূর্ণ concept-গুলোর একটি।

Idea:

> Resource object-এর lifetime-এর সাথে bind থাকবে।

---

উদাহরণ:

```cpp
class File
{
public:
    File()
    {
        OpenFile();
    }

    ~File()
    {
        CloseFile();
    }
};
```

Object destroy হলেই resource release হবে।

---

# Smart Pointer

Modern C++-এ raw `new/delete` কম ব্যবহার করা হয়।

---

## unique_ptr

```cpp
auto dog = std::make_unique<Dog>();
```

Destroy automatically:

```cpp
Scope End
    ↓
Destructor Called
    ↓
Memory Released
```

---

## shared_ptr

একাধিক owner থাকলে:

```cpp
std::shared_ptr<Dog>
```

ব্যবহার করা হয়।

Reference count শূন্য হলে object destroy হয়।

---

# Static Object Lifetime

```cpp
static Dog dog;
```

Lifetime:

```text
Program Start
    ↓
Create
    ↓
Program Running
    ↓
Program Exit
    ↓
Destroy
```

---

# Singleton এবং Static Lifetime

অনেক Singleton implementation:

```cpp
class Logger
{
public:
    static Logger& GetInstance()
    {
        static Logger instance;
        return instance;
    }
};
```

এখানে:

```cpp
static Logger instance;
```

পুরো program lifetime জুড়ে বেঁচে থাকে।

---

# Embedded Systems-এ কেন গুরুত্বপূর্ণ?

SMT machine, robotics, motion controller, automotive systems-এর মতো environment-এ:

* Heap allocation কম ব্যবহার করা হয়
* Memory fragmentation avoid করা হয়
* Object pools ব্যবহার করা হয়
* Pre-allocated memory blocks ব্যবহার করা হয়
* Deterministic execution গুরুত্বপূর্ণ

এই কারণেই অনেক embedded project-এ:

```cpp
new
delete
```

সীমিতভাবে ব্যবহার করা হয়।

---

# Summary

একটি C++ object সাধারণত চার ধরনের lifetime-এর মধ্যে পড়ে:

| Type            | Location       | Lifetime        |
| --------------- | -------------- | --------------- |
| Local Variable  | Stack          | Scope পর্যন্ত   |
| Dynamic Object  | Heap           | delete পর্যন্ত  |
| Global Variable | Global Segment | Program পর্যন্ত |
| Static Variable | Static Segment | Program পর্যন্ত |

C++-এর references, pointers, polymorphism, smart pointers, singleton, factory pattern, object pool এবং embedded architecture বুঝতে হলে Stack, Heap, Static Memory এবং Object Lifetime সম্পর্কে পরিষ্কার ধারণা থাকা অত্যন্ত গুরুত্বপূর্ণ।
