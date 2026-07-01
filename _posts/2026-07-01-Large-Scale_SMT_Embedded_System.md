---
title: "👀Understanding a Large-Scale SMT Embedded System: RTOS Tasks, State Machines, Events, and Coordinators👛👛"
date: 2026-07-01
layout: single
categories:
  - engineering
---
# Understanding a Large-Scale SMT Embedded System: RTOS Tasks, State Machines, Events, and Coordinators

## Overview

এই নোটটি একটি production-grade SMT (Surface Mount Technology) machine software architecture বিশ্লেষণের উপর ভিত্তি করে লেখা।

প্রথমদিকে আমার ধারণা ছিল:

```text
Many Tasks = Many CPU Cores
```

কিন্তু codebase analysis করার পরে বুঝলাম বাস্তবতা সম্পূর্ণ ভিন্ন।

এই system-এর complexity মূলত:

* CPU core count থেকে আসে না
* File count থেকেও পুরোপুরি আসে না

বরং আসে:

```text
Events
Triggers
State Machines
Coordinators
RTOS Tasks
Inter-Module Communication
```

এর interaction থেকে।

---

# System Architecture Summary

## Platform

```text
MCU Family:
Renesas SH-4A

RTOS:
ITRON 4.0 / PrKERNEL

Execution Model:
Preemptive RTOS
```

```text
1 MCU Board
=
1 CPU Core
=
Many Concurrent RTOS Tasks
```

---

# Single Core ≠ Single Task

প্রথমদিকে অনেক engineer-এর মতো আমিও ভেবেছিলাম:

```text
1 Core
=
1 Task
```

বাস্তবে:

```text
1 Core
=
Many Tasks
+
RTOS Scheduler
```

উদাহরণ:

```text
Alarm Task
Motion Task
Conveyor Task
Network Task
Coordinator Task
HMI Task
```

সবগুলো একই CPU Core ব্যবহার করে।

---

# Concurrency vs Parallelism

## Concurrency

এই system-এর primary execution model:

```text
Task A
↓
Context Switch
↓
Task B
↓
Context Switch
↓
Task C
```

CPU খুব দ্রুত task পরিবর্তন করে।

ফলে মনে হয় সবকিছু একসাথে চলছে।

এটিই Concurrency.

---

## Parallelism

Parallelism মানে:

```text
Core 1 → Task A
Core 2 → Task B
Core 3 → Task C
```

অর্থাৎ সত্যিকারের simultaneous execution।
---

# Twin Robot Configuration

একটি গুরুত্বপূর্ণ discovery:

```text
CPU1
CPU2
```

দেখে প্রথমে multi-core মনে হতে পারে।

কিন্তু বাস্তবে:

```text
CPU1 = Separate Processor Board
CPU2 = Separate Processor Board
```

অর্থাৎ:

```text
Twin Robot
=
Two Independent MCU Boards
```

এক chip-এর দুই core নয়।

---

# Practical Mental Model

Single Robot:

```text
1 MCU Board
↓
1 Core
↓
~175 RTOS Tasks
```

Twin Robot:

```text
CPU1 Board
↓
~175 Tasks

CPU2 Board
↓
~175 Tasks
```

Communication হয়:

```text
Events
DIO
Inter-CPU Communication
```

এর মাধ্যমে।

---

# RTOS Task Count

Codebase scan অনুযায়ী:

```text
OSCreateTask()
```

call count:

| Scope                           | Count |
| ------------------------------- | ----: |
| Module / ModuleClasses          |   175 |
| Module + Base + Panel + CommHMI |  ~208 |
| RTOS Maximum Limit              |   400 |

RTOS Configuration:

```cpp
#define OS_TASK_KIND_MAXX (400)
```

---

# Important Realization

অনেক engineer শুরুতে ভুল করে ধরে নেয়:

```text
State Class
=
RTOS Task
```

কিন্তু এই system-এ:

```text
CState*
CCoordinator*
```

সাধারণত RTOS Task নয়।

বরং:

```text
Existing RTOS Task
↓
Receives Event
↓
Calls Active()
↓
State Machine Executes
```

---

# Emergency Stop Example

Flow:

```text
Sensor Detects Error
↓
EMG Watching Task
↓
OSSendEvent(EVENT_ALARM_STOP)
↓
State Machine Task Receives Event
↓
Trigger Assigned
↓
CStaAlarmStoping::Active()
↓
Machine Stops
```

---

# State Machine Scale

Codebase analysis:

| Item                         |  Count |
| ---------------------------- | -----: |
| Trigger IDs                  |    176 |
| Event IDs                    | ~2,888 |
| State Classes                |    118 |
| State Implementations        |    285 |
| Manufacturing Trigger States |     95 |

---

# Coordinator Scale

| Item                        | Count |
| --------------------------- | ----: |
| Coordinator Classes         |   834 |
| Coordinator Base Classes    |    48 |
| Coordinator Implementations | 1,129 |

---

# Unit Layer Scale

| Item           | Count |
| -------------- | ----: |
| Unit Headers   |   582 |
| Unit CPP Files |   818 |

---

# Event System Scale

Event count:

```text
~2,888 EVENT_* definitions
```

Maximum supported:

```cpp
OS_EVENT_ID_MAX = 16384
```

এই system-এর communication backbone মূলত Event Architecture।

---

# Trace Layer

Debugging-এর সময় তিনটি layer track করা সবচেয়ে গুরুত্বপূর্ণ:

```text
Trace Object
Trigger
Event
```

উদাহরণ:

```text
TraceID.h Object No
↓
TRIGGER_*
↓
EVENT_*
```

এই তিনটি layer অনুসরণ করলে বেশিরভাগ runtime behavior trace করা যায়।

---

# Conceptual State Hierarchy

```text
CStateMachine
│
├── CStateAutopilot
├── CStateWorking
├── CStateWaitingBoard
│
├── CStateAbnormalMonitoring
│     │
│     └── CStateAbnormalStop
│            │
│            ├── CStateAlarmStop
│            ├── CStateMotionStop
│            ├── CStateHandPoweredEmergencyStop
│            └── ...
│
└── CStateAbnormalRemoveControler
```

---

# What Makes This System Large?

Initially I assumed:

```text
More CPU
=
More Complexity
```

After analysis:

```text
Complexity
≠ Core Count
```

Real complexity comes from:

```text
175 RTOS Tasks
+
176 Triggers
+
2888 Events
+
118 State Classes
+
834 Coordinators
+
Inter-CPU Communication
```

and the relationships between them.

---

# Most Useful Mental Model

Instead of thinking:

```text
CPU
Register
Clock Cycle
Instruction
```

I found it more useful to think:

```text
Physical Event
↓
Sensor Input
↓
RTOS Task Wakeup
↓
Event Generation
↓
Trigger Selection
↓
State Transition
↓
Coordinator Action
↓
Machine Behavior Change
```

---

# Key Engineering Takeaway

For large SMT embedded systems:

```text
CPU executes instructions
RTOS schedules tasks
Events drive communication
Triggers select behavior
State Machines control flow
Coordinators synchronize modules
```

The machine is not primarily a collection of variables or files.

It is a network of:

```text
Tasks
Events
States
Coordinators
```

working together to transform real-world machine behavior into deterministic software behavior.

