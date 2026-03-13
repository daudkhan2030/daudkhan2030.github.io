---
title: "General SMT Architectural Layers"
date: 2026-03-13
layout: single
categories:
  - engineering
---

🏭 SMT Based সিস্টেমে কোন কোন Architectural Layer থাকে?

বড় SMT machine software সাধারণত layered architecture follow করে।
Codebase এর directory structure, module naming এবং include dependency দেখে roughly এই ধরনের layer structure বোঝা যায়।

🖥️ 1️⃣ Application / HMI Layer
(Operator Interaction Layer)

কাজ:

- Operator UI
- Error / Alarm panel
- NPI UI tools
- Machine interaction screens

এই layer মূলত operator interaction এবং visualization handle করে।

🧠 2️⃣ Coordinator / Domain Logic Layer
(Workflow Control Layer)

কাজ:

- Job flow control
- Test sequence orchestration
- Abnormal release sequence
- Production workflow coordination

এই layer machine operation এর core process logic orchestrate করে।

⚙️ 3️⃣ Unit / Machine Model Layer
(Machine Representation Layer)

কাজ:

- Machine এর logical structure model করা।

উদাহরণ:

- Lane
- Placement Head
- Feeder
- Tray
- Part information

এই layer-এ physical machine components কে software model হিসেবে represent করা হয়।

📦 4️⃣ Infrastructure / Service Layer
(Shared System Services)

কাজ:

- Test result XML generation
- Remote command handling
- Network file access
- Trace / logging system

এই layer system-wide shared services provide করে যেগুলো multiple modules ব্যবহার করে।

🔌 5️⃣ Platform / HAL / Communication Layer
(Hardware Integration Layer)

কাজ:

- Hardware communication abstraction
- Network setup / communication middleware
- Virtual IO handling
- Shared memory access

এই layer মূলত hardware communication এবং system integration handle করে।

🧩 6️⃣ RTOS / OS Abstraction Layer
(Operating System Interface Layer)

অনেক industrial system-এ OS abstraction layer থাকে যাতে একই codebase বিভিন্ন environment-এ run করা যায়।

কাজ:

- Task / Thread management
- Delay / timing control
- Mutex / synchronization
- System utilities

এই layer সাধারণত RTOS এবং Windows simulation environment উভয়ের জন্য abstraction provide করে।

🧪 7️⃣ Simulation Layer
(Hardware Emulation Layer)

কাজ:

- Hardware simulation modules
- Dummy drivers
- Trace logging during simulation

এই layer ব্যবহার করে actual hardware ছাড়াই system behaviour test করা যায়।

📊 Architecture Summary

SMT machine software সাধারণত ~7টা architectural layer এ logically separate করা যায়।

যদিও কিছু layer-এর responsibility overlap করতে পারে, কিন্তু API boundary perspective থেকে এই layered separation system architecture বুঝতে খুব helpful।
