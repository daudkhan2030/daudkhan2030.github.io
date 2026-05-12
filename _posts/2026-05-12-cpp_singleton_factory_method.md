---
title: "🧩 C++ Notes: Static, Singleton, Factory Method & Struct Concepts"
date: 2026-05-11
layout: single
categories:
  - systems
---

🔍 **C++ Design Notes from Legacy Codebase Exploration**

Recently while exploring a legacy C++/SMT machine codebase, I tried to simplify some confusing concepts like:

- `static`
- `Singleton`
- `Factory Method`
- object vs pointer behavior
- C vs C++ struct differences

এই post-এ সেগুলার beginner-friendly Bangla notes লিখে রাখলাম future reference-এর জন্য।

---

# 🧠 Few Shortcuts to Remember

- যেসবে `&` ইউজ করা হয় সেগুলা সাধারণত বড় object হয়।
- বড় object copy না করে `pass by reference` করা হয় performance save করার জন্য।
- অনেক legacy project-এ C style struct এখনো heavily use হয়।

---

# 🌸 C Struct vs C++ Struct

---

## ✅ C++ Struct

```cpp
struct T_ROW_AVL_DATA
{
    SHORT shFeederIndex;
    SHORT shSlotNo;
    SHORT shSubSlotNo;
    CHAR  szTrayPos[TRAY_POS_LEN];
    CHAR  szAVLName[PROG_AVLNAME_AREA];
};
✅ C Struct
typedef struct
{
    CHAR  szFeedPitch[FEED_PITCH_LEN];
    CHAR  szTapeWidth[TAPE_WIDTH_LEN];
    SHORT shTrayColQty;
    SHORT shTrayRowQty;
    SHORT shPartDirection;
    CHAR  szDeviceComment[PROG_BARCODELABEL_AREA];
    CHAR  szPartComment[PROG_PARTCOMMENT_AREA];
} T_FEEDERSETUP_DATA;
🧠 Important Shortcut

অনেক legacy C project-এ:
typedef struct
ব্যবহার করা হয় কারণ C language-এ:

struct TEST
লিখে variable declare করতে হয়।

তাই typedef দিয়ে shorthand বানানো হয়।

🔒 Private Constructor
private:
    Logger() {}

যদি constructor private হয় তাহলে:

- class-এর বাইরে থেকে object create করা যাবে না
- controlled object creation enforce করা যায়

এটা সাধারণত Singleton pattern implement করার সময় use করা হয়।

🌸 Singleton Design Pattern

Singleton-এর main idea:

পুরো system-এ শুধুমাত্র ১টা object থাকবে।
কিন্তু এর মানে এটা না যে:
একসাথে এক জায়গায়ই কাজ করবে ❌

বরং:

same object অনেক জায়গা থেকে use হতে পারে ✅
অনেক class একই object access করতে পারে ✅

🧩 Singleton Example

class Logger {
private:
    static Logger* s_instance;
    Logger() {}

public:
    static Logger* GetInstance() {

        if (!s_instance)
            s_instance = new Logger();

        return s_instance;
    }
};

🧠 GetInstance() এর Main Idea

Logger::GetInstance()->Write();

এটা:
100টা class থেকেও call হতে পারে

তবে:
object একটাই
multiple copy/object create হয় না

⚡ Why GetInstance() Uses static
static Logger* s_instance;

এখানে:
s_instance হলো shared pointer
পুরো class-এর জন্য only one copy থাকে

তাই:
Logger::GetInstance()

যেখান থেকেই call করো,
সবাই same object পায়।

🧠 static এর আসল তাৎপর্য

অনেকে ভাবে:
static মানে only one object ❌

আসলে:
static মানে shared copy ✅

🔍 Example
class Test {
public:
    static int count;
};
Test a;
Test b;

এখানে:
a এবং b দুইটা আলাদা object
কিন্তু count একটাই shared variable

তাই:
a.count
b.count

দুটোই same memory access করে।

কারণ: count কে static করা হয়েছে।

🧠 Important Understanding
static নিজে Singleton না।

বরং:

private constructor
controlled creation
shared static instance

সব মিলিয়ে Singleton pattern তৈরি হয়।

🌸 Factory Method Pattern
🧩 Basic Example
class Product {};

class Factory {
public:
    virtual Product* Create() = 0;
};

class AFactory : public Factory {
public:
    Product* Create() override {
        return new Product();
    }
};

🧠 Components
Pattern Part	Class
Creator	Factory
Concrete Creator	AFactory
Product	Product

🔍 How It Works
Factory* f = new AFactory();
Product* p = f->Create();

- এখানে caller জানেই না internally: new Product() হচ্ছে।
- Factory নিজেই object create করে caller-কে return করে।

🔥 Why Factory Method Used?

- Caller যেন direct: new Product() না করে।

কারণ future-এ creation logic complex হতে পারে:

initialization লাগতে পারে
config লাগতে পারে
pool থেকে নিতে হতে পারে
different type return হতে পারে

এসব caller না জেনেও object use করতে পারবে।

🧠 Problem Solved by Factory Method

✅ object creation centralized হয়
✅ caller dependency কমে
✅ future modification সহজ হয়
✅ creation logic এক জায়গায় থাকে

🎯 Key Insight

“তুমি শুধু factory-কে বলো object লাগবে, factory নিজেই decide করবে কিভাবে সেটা বানাবে।”

🚀 Final Takeaway

এই concepts গুলা legacy C++ system-এ খুব frequently দেখা যায়:

Singleton
Factory Method
static shared state
controlled object creation
abstraction-based object handling

বিশেষ করে:

embedded systems
SMT machine software
large scale C++ applications

এগুলোতে design patterns heavily use করা হয় maintainability এবং scalability-এর জন্য।

#Cpp #DesignPatterns #Singleton #FactoryMethod #EmbeddedSystems #LegacyCode #OOP #SoftwareDesign
