---
title: "🌸 C++ Fundamentals: References, Pointers, Memory and Object Access"
date: 2026-06-03
layout: single
categories:
    - notes
---

## Introduction

C++ শেখার সময় অনেক developer প্রথমে variables, functions এবং classes নিয়ে কাজ শুরু করে। কিন্তু C++-এর আসল শক্তি বোঝার জন্য memory model, references এবং pointers সম্পর্কে পরিষ্কার ধারণা থাকা অত্যন্ত গুরুত্বপূর্ণ।

বড় embedded systems, SMT machines, robotics software, game engines কিংবা ADAS systems—সব জায়গাতেই references এবং pointers ব্যাপকভাবে ব্যবহৃত হয়। তাই এই post-এ C++-এর কিছু fundamental concept সহজভাবে আলোচনা করা হলো।

---

## Variable এবং Memory

ধরি:

```cpp
int a = 10;
```

এখানে `a` একটি object।

Memory-তে এরকম কিছু হতে পারে:

```text
Address    Value
0x100      10
```

Variable মূলত memory-র একটি নির্দিষ্ট location-এর নাম।

---

## Reference (Alias)

Reference হলো কোনো existing object-এর আরেকটি নাম।

```cpp
int a = 10;
int& b = a;
```

এখানে `b` নতুন object নয়।

বরং:

```text
a ----+
      |
b ----+
```

দুটো নাম একই object-কে refer করছে।

যদি:

```cpp
b = 20;
```

তাহলে:

```cpp
a == 20
```

কারণ `b` এবং `a` একই object।

---

## Reference Chain

```cpp
int a = 10;

int& b = a;
int& c = b;
```

এখানে:

```text
a ----+
      |
b ----+
      |
c ----+
```

সবগুলো একই object-কে refer করছে।

```cpp
c = 30;
```

এর ফলে:

```cpp
a == 30
b == 30
c == 30
```

---

## Pointer

Pointer হলো এমন একটি variable যা অন্য কোনো object-এর address store করে।

```cpp
int a = 10;

int* p = &a;
```

Memory:

```text
0x100 : a = 10

0x200 : p = 0x100
```

এখানে `p`-এর value হলো `a`-এর address।

---

## Address Operator (&)

```cpp
&a
```

মানে:

> "a-এর address"

উদাহরণ:

```cpp
cout << &a;
```

Output:

```text
0x100
```

---

## Dereference Operator (*)

```cpp
*p
```

মানে:

> "p যেই address store করে সেখানে গিয়ে value access করো"

উদাহরণ:

```cpp
int a = 10;

int* p = &a;

cout << *p;
```

Output:

```text
10
```

---

## Pointer দিয়ে Value পরিবর্তন

```cpp
int a = 10;

int* p = &a;

*p = 50;
```

Result:

```cpp
a == 50
```

কারণ pointer-এর মাধ্যমে original object modify করা হয়েছে।

---

## Reference vs Pointer

Reference:

```cpp
int& r = a;
```

Pointer:

```cpp
int* p = &a;
```

দুটো দিয়েই original object modify করা যায়।

```cpp
r = 20;
*p = 20;
```

দুটোই `a` পরিবর্তন করবে।

কিন্তু তাদের capability এক নয়।

---

## Reference Rebind করা যায় না

```cpp
int a = 10;
int b = 20;

int& r = a;
```

এখন:

```cpp
r = b;
```

এটি reference redirect করবে না।

বরং:

```cpp
a = b;
```

execute হবে।

Reference এখনও `a`-কেই refer করবে।

---

## Pointer Redirect করা যায়

```cpp
int a = 10;
int b = 20;

int* p = &a;
```

এখন:

```cpp
p = &b;
```

Pointer এখন `b`-কে refer করবে।

---

## Null Pointer

Pointer:

```cpp
int* p = nullptr;
```

Valid।

Reference:

```cpp
int& r;
```

Invalid।

Reference সবসময় valid object-এর সাথে bind হতে হবে।

---

## Pass By Value

```cpp
void Foo(int x)
{
    x = 100;
}
```

Original object modify হবে না।

কারণ copy তৈরি হয়।

---

## Pass By Reference

```cpp
void Foo(int& x)
{
    x = 100;
}
```

Original object modify হবে।

---

## Pass By Pointer

```cpp
void Foo(int* x)
{
    *x = 100;
}
```

Call:

```cpp
Foo(&a);
```

Original object modify হবে।

---

## Const Reference

Modern C++-এ সবচেয়ে বেশি দেখা যায়:

```cpp
void Print(const string& str)
{
}
```

কারণ:

```cpp
void Print(string str)
```

string copy করবে।

কিন্তু:

```cpp
const string&
```

copy করবে না।

Performance ভালো হবে।

---

## Arrays এবং Pointer

```cpp
int arr[3] = {10,20,30};
```

প্রায়শই:

```cpp
arr == &arr[0]
```

সত্য।

কারণ array-এর নাম প্রথম element-এর address represent করে।

---

## Object Pointer

```cpp
class Dog
{
public:
    void Bark()
    {
    }
};
```

```cpp
Dog d;

Dog* p = &d;
```

Member access:

```cpp
p->Bark();
```

এটি মূলত:

```cpp
(*p).Bark();
```

এর shortcut।

---

## This Pointer

প্রতিটি non-static member function-এর একটি hidden pointer থাকে:

```cpp
this
```

উদাহরণ:

```cpp
class Dog
{
public:
    int age;

    void SetAge(int age)
    {
        this->age = age;
    }
};
```

`this` বর্তমান object-কে নির্দেশ করে।

---

## Polymorphism এবং Base Pointer

```cpp
class Animal
{
public:
    virtual void Speak() {}
};
```

```cpp
class Dog : public Animal
{
public:
    void Speak() override
    {
        cout << "Woof";
    }
};
```

```cpp
Animal* p = new Dog();

p->Speak();
```

Runtime-এ Dog-এর function call হবে।

এটাই runtime polymorphism-এর foundation।

---

## Embedded Systems এবং Large Applications-এ সবচেয়ে বেশি ব্যবহৃত Concepts

### References

```cpp
void Process(Job& job)
```

### Const References

```cpp
void Process(const Job& job)
```

### Object Pointers

```cpp
Device* dev;
```

### Base Class Pointers

```cpp
IDevice* dev;
```

### Null Checks

```cpp
if(dev != nullptr)
{
}
```

### This Pointer

```cpp
this->m_state
```

### Smart Pointers

```cpp
std::unique_ptr<T>
std::shared_ptr<T>
```

---

## Conclusion

References এবং pointers দুটোই memory access-এর powerful mechanism।

Reference মূলত alias হিসেবে ব্যবহৃত হয় এবং function parameter passing-এ সবচেয়ে বেশি দেখা যায়।

Pointer address manipulation, dynamic memory management, polymorphism, ownership handling এবং complex system design-এর foundation হিসেবে ব্যবহৃত হয়।

এই conceptগুলো ভালোভাবে বুঝতে পারলে Factory Pattern, Dependency Injection, Object Pool, Singleton, STL Containers, Embedded Frameworks এবং Large Scale C++ Applications অনেক সহজে বোঝা যায়।
