---
title: "🚀 Cursor AI Codebase Indexing Optimization Guide"
date: 2026-04-09
layout: single
categories:
  - notes
---
# 🚀 Cursor AI Codebase Indexing Optimization Guide

## 🔹 Overview

এই গাইডটি **Cursor AI ব্যবহার করে large codebase efficiently index করার জন্য** তৈরি করা হয়েছে।
Proper setup না থাকলে indexing slow, stuck বা irrelevant file include হতে পারে।

👉 তাই এখানে clean, optimized এবং production-level workflow দেওয়া হলো।

---

# 🧹 1. Files that need to be deleted before indexing

কার্সর ইন্ডেক্সিং করার আগে নিচের ফাইলগুলো delete করা recommended — কারণ এগুলো AI learning-এর জন্য useless।

---

## 📦 Compiled Files (Binary / runtime files)

```
.dll
*.exe
*.so
*.a
*.lib
*.bin
*.out
```

---

## ⚙️ Object / Build Artifacts

```
.o
*.obj
*.pdb
*.ilk
*.idb
```

---

## 🏗️ Build system generated folders

```
/build/
/out/
/bin/
/Debug/
/Release/
/x64/
/Win32/
```

---

## 📁 Installer / Package junk

```
.msi
*.cab
*.zip
*.7z
*.tar
*.gz
```

---

## 🧾 Logs / Runtime data

```
.log
*.trace
*.dmp
*.tmp
```

---

## 🤖 Auto-generated source (conditionally)

```
*_autogen._generated.*
*.pb.cc
*.pb.h
```

---

# ⚡ 2. Delete Old Index and Upload New One (Shortcut Command)

Manual delete করার পরিবর্তে নিচের command run করলেই সব unwanted files delete হয়ে যাবে:

```bash
for /r %i in (*.dll *.exe *.so *.a *.lib *.bin *.out *.o *.obj *.pdb *.ilk *.idb *.msi *.cab *.zip *.7z *.tar *.gz *.log *.trace *.dmp *.tmp *.pb.cc *.pb.h) do del /q "%i"
```

👉 এটি recursively সব folder scan করে unwanted files delete করবে।

---

# 🔥 3. FULL HARD RESET (Must Follow)

## Step 1: Cursor kill করো

Task Manager →

* Cursor.exe
* Cursor Helper
  👉 End Task

---

## Step 2: Cursor data delete করো

### Roaming

```
C:\Users\<user>\AppData\Roaming\Cursor
```

### Local

```
C:\Users\<user>\AppData\Local\Cursor
```

👉 ⚠️ পুরো `Cursor` folder delete করো

---

## Step 3: Temp clean (optional)

```
Win + R → %temp%
```

---

## Step 4: PC Restart 🔁

👉 Must (skip কোরো না)

---

# 🔄 4. Process of deleting Cursor data before re-indexing

👉 যখন পুরানো project index remove করে নতুন project index করতে চাও:

1. Cursor close করো
2. Cursor data (Roaming + Local) delete করো
3. PC restart করো
4. Cursor open করো
5. Home page → New Project → folder select করো
6. indexing auto শুরু হবে

---

# 🧠 5. .cursorignore (Best Practice)

`.cursorignore` হলো এমন একটি file যা Cursor-কে বলে দেয় কোন file/folder ignore করতে হবে।

---

## 📁 Location

👉 Project root folder-এ রাখতে হবে

```
C:\dev\NXT_Copy\.cursorignore
```

---

## 📄 Content of .cursorignore

```bash
# Build folders
build/
out/
bin/
Debug/
Release/
x64/
Win32/

# Logs & temp
# Binary / compiled
# Archives
# Generated files
*.dll
*.exe
*.so
*.a
*.lib
*.bin
*.out
*.o
*.obj
*.pdb
*.ilk
*.idb
*.msi
*.cab
*.zip
*.7z
*.tar
*.gz
*.log
*.trace
*.dmp
*.tmp
*.pb.cc
*.pb.h
*.LOG
*.TMP
*.cache
*.db
*.sdf
*.opensdf
*.VC.db

# Heavy folders (if exist)
node_modules/
.cache/
```

---

## 🎯 Benefit

👉 `.cursorignore` থাকলে:

* ❌ manually delete দরকার নেই
* ❌ unnecessary file index হবে না
* ✔ fast indexing
* ✔ clean AI context

---

# ✅ Final Workflow

👉 Best practice:

1. `.cursorignore` add করো
2. project open করো
3. indexing start করো

👉 optional:

* cleanup command run
* hard reset (if issue)

---

# 🔑 Conclusion

👉 Cursor AI efficiently use করতে চাইলে:

* unwanted files remove বা ignore করতে হবে
* clean indexing environment maintain করতে হবে

✔ Proper setup = faster + smarter code understanding
✔ Better AI responses
✔ No indexing issues

---

🚀 Happy Coding with Cursor AI!
