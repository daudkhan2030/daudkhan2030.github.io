---
title: "👛👀 Autoware Architecture: Sensor থেকে Vehicle Control পর্যন্ত End-to-End Flow"
date: 2026-07-29
layout: single
categories:
  - engineering
---
Autoware শেখা শুরু করার সময় আমার সবচেয়ে বড় প্রশ্ন ছিল:

> "গাড়ি কীভাবে lane ধরে রাখে? Camera কীভাবে Planning-এর সাথে যুক্ত হয়? শেষ পর্যন্ত Steering ECU পর্যন্ত command কীভাবে পৌঁছায়?"

অনেক documentation পড়ার পর আমি Autoware-এর end-to-end execution flow এভাবে বুঝেছি।

---

# ১. Physical Sensor Layer

Autoware-এর শুরু Camera বা LiDAR node দিয়ে নয়, বরং গাড়ির **physical hardware sensors** দিয়ে।

যেমন:

* Camera
* LiDAR
* Radar
* IMU
* GPS
* Wheel Encoder

এগুলো বাস্তব sensor, Autoware-এর virtual node নয়।

তবে গুরুত্বপূর্ণ বিষয় হলো, এই sensor-গুলো সরাসরি ROS2 topic publish করে না।

প্রতিটি sensor-এর জন্য একটি **Driver Node** থাকে।

উদাহরণ:

```text
Physical Camera
        │
        ▼
Camera Driver Node
        │
        ▼
/camera/image_raw
```

একইভাবে,

```text
Physical LiDAR
        │
        ▼
LiDAR Driver Node
        │
        ▼
/points_raw
```

অর্থাৎ ROS2 topic publish করে Driver Node, Sensor নিজে নয়।

---

# ২. Perception Layer

Driver Node থেকে আসা raw data বিভিন্ন Perception Node subscribe করে।

উদাহরণ:

LiDAR Driver publish করল:

```text
/points_raw
```

Object Detection Node:

```text
Subscribe
   ↓
Ground Removal
   ↓
Point Cloud Clustering
   ↓
Object Detection
   ↓
Object Classification
   ↓
Publish
```

Publish করতে পারে:

```text
/objects
```

Camera-এর ক্ষেত্রেও একই ধারণা।

```text
Camera Driver
   ↓
/camera/image_raw
   ↓
Lane Detection
   ↓
Traffic Sign Detection
   ↓
Object Detection
   ↓
Publish
```

অর্থাৎ Driver Node raw sensor data publish করে এবং Perception Node সেই data process করে নতুন topic publish করে।

---

# ৩. Localization Layer

Localization একাধিক sensor-এর data একত্র করে গাড়ির বর্তমান অবস্থান নির্ণয় করে।

Input:

* GPS
* IMU
* Wheel Encoder

Output:

* Current Pose
* Vehicle Heading
* Velocity

এগুলো ROS2 topic হিসেবে publish হয়।

---

# ৪. Planning Layer

Planning একসাথে অনেক topic subscribe করে।

যেমন:

* Current Pose
* HD Map
* Lane Information
* Detected Objects
* Mission Goal

Planning-এর কাজ হলো:

* কোন lane follow করতে হবে
* Lane change দরকার কিনা
* সামনে obstacle আছে কিনা
* Speed কত হওয়া উচিত
* কোন trajectory follow করতে হবে

Planner সিদ্ধান্ত নেয় এবং একটি trajectory তৈরি করে।

Trajectory সাধারণত অনেকগুলো point নিয়ে গঠিত থাকে।

প্রতিটি point-এ থাকতে পারে:

* X
* Y
* Velocity
* Heading (Yaw)

এরপর Planner trajectory publish করে।

---

# ৫. Control Layer

Control Node subscribe করে:

* Trajectory
* Current Vehicle Pose

এরপর Control algorithm calculate করে:

* Steering Angle
* Acceleration
* Brake

তারপর Control Command publish করে।

---

# ৬. Vehicle Interface

Vehicle Interface Node Control Command receive করে।

এরপর সেই command-কে Vehicle Communication Protocol-এ রূপান্তর করে।

যেমন:

* CAN
* CAN FD
* Automotive Ethernet

এরপর message Vehicle ECU-তে পাঠানো হয়।

---

# ৭. ECU Layer

Vehicle ECU command receive করে।

উদাহরণ:

* Steering ECU
* Brake ECU
* Powertrain ECU

ECU low-level actuator control করে।

যেমন:

* Steering Motor
* Brake Actuator
* Throttle Actuator

---

# ৮. Closed Feedback Loop

Autoware একবার command পাঠিয়ে থেমে যায় না।

Vehicle movement-এর পর sensor আবার নতুন data collect করে।

সেই data আবার Driver Node publish করে।

তারপর:

```
Perception
   ↓
Localization
   ↓
Planning
   ↓
Control
   ↓
Vehicle Interface
   ↓
ECU
   ↓
Vehicle Motion
   ↓
Sensors
   ↓
Perception...
```

এই loop continuously চলতে থাকে।
---

# ৯. Autoware এবং ROS2-এর সম্পর্ক

Autoware এবং ROS2 একই জিনিস নয়।

তাদের relationship হলো:

```text
Autoware
        │
        ▼
Uses ROS2 APIs
        │
        ▼
ROS2 Middleware
        │
        ▼
Ubuntu Linux
        │
        ▼
Compute Platform
```

Autoware হলো Autonomous Driving Application।

ROS2 হলো Middleware।

Ubuntu Linux হলো Operating System।

---

# ১০. Autoware-এর মূল দায়িত্ব

Autoware-এর কাজ শুধুমাত্র Trajectory publish করা নয়।

এর প্রধান দায়িত্ব:

* Sensor Data Processing
* Localization
* Perception
* Behavior Planning
* Motion Planning
* Vehicle Control
* Emergency Decision
* Vehicle Command Generation

সবশেষে Vehicle Interface-এর মাধ্যমে ECU-তে command পাঠানো হয়।

---

# End-to-End Flow

```text
Physical World
        │
        ▼
Physical Sensors
        │
        ▼
Driver Nodes
        │
        ▼
ROS2 Topics
        │
        ▼
Localization
 Perception
  Planning
   Control
    AEB
        │
        ▼
Vehicle Interface
        │
        ▼
CAN / Automotive Ethernet
        │
        ▼
Vehicle ECU
        │
        ▼
Steering / Brake / Throttle
        │
        ▼
Vehicle Motion
        │
        ▼
Sensors Measure Again
        │
        └───────────────► Repeat
```

---

## আমি যা শিখলাম

Autoware কোনো HMI application নয়।

এটি ROS2-এর উপর নির্মিত একটি Autonomous Driving Software Stack, যেখানে অসংখ্য ROS2 Node একে অপরের সাথে Publish/Subscribe mechanism-এর মাধ্যমে যোগাযোগ করে।

প্রতিটি module একটি নির্দিষ্ট দায়িত্ব পালন করে এবং সব module মিলে নিরাপদভাবে গাড়ি চালানোর সিদ্ধান্ত নেয়।

সবশেষে সেই সিদ্ধান্ত Vehicle Interface-এর মাধ্যমে ECU-তে পৌঁছে যায় এবং ECU বাস্তব actuator নিয়ন্ত্রণ করে।
