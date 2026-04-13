---
title: "🚀 Cursor AI Chat Logger (Auto Timestamp + Tagging সহ)"
date: 2026-04-13
layout: single
categories:
  - notes
---

📌 Overview

আমি Cursor AI দিয়ে local indexed project-এ কাজ করার সময় একটা বড় problem face করছিলাম:

👉 Chat history persist থাকে না
👉 Important prompts / debugging insights হারিয়ে যায়

এই problem solve করার জন্য আমি একটা Python-based automated clipboard logger system বানিয়েছি।

🎯 Problem
Cursor local mode → no chat export
No Git / no remote repo
Conversations are temporary

➡️ Result: Knowledge loss

💡 Solution

A fully local automation system that:

Clipboard monitor করে
Cursor থেকে copy করা text auto detect করে
Markdown file-এ save করে
Manual tagging support দেয়
⚙️ Features
✅ Auto logging (clipboard monitoring)
🕒 Timestamp (auto generated)
🏷️ Tagging system (Ctrl + Shift + S)
📄 Markdown structured log
🔁 Duplicate prevention
🛠️ Tech Stack
Python
pyperclip
keyboard
📂 Project Structure

```
automation/
├── clipboard_logger.py
├── cursor_chat_log.md
└── run_logger.bat
```
▶️ Setup Guide
1. এই পাইথন বেজড সিস্টেম আমার কার্সরে রেসপন্স কপি ক্লিপবোর্ড থেকে নিয়ে নোট করবে ।
- প্রথমে পাইথন ইন্সটল দিয়ে পাথ অ্যাড করতে হবে ।
- https://www.python.org/downloads/ এখান থেকে পাইথন ডাউনলোড করে ইন্সটল করতে হবে । এরপরে পাথ অ্যাড ।

<img width="856" height="542" alt="image" src="https://github.com/user-attachments/assets/8f363cca-6bdc-4a1e-9f31-312647d96cd7" />

- এখানে আমার পাইথন ইন্সটল করা আছে । এই URL পাথ হিসেবে দিবো ।
- python —version এটা cmd তে রান করে দেখবো ।
- যদি ভার্শন দেখায় তাহলে ওকে । নাহলে Start —> ‘edit the system environement variables’ এ যেয়ে পাথ চেঞ্জ করবো ।

<img width="1913" height="487" alt="image" src="https://github.com/user-attachments/assets/0d220944-c48a-4287-9212-c0e6760fbc34" />
- এভাবে উপরের মত করে অ্যাড করা লাগবে।
- আর যদি উপরের উয়িন্ডোজ থেকে সেট থাকে তাহলে সেটাতে কাজ হবে না । নতুন করে সেট করা লাগবে ।
- নিচের where python হলো আসল পাথ . where py এর পাথে কাজ নাই ।

- py -m ensurepip --upgrade যেহেতু pip ইন্সটল নাই তাই ইন্সটল করবো ।
- if installed then below will be showing

<img width="830" height="874" alt="image" src="https://github.com/user-attachments/assets/83090037-1ab1-4f71-aa5e-3886752a99c4" />

- এখানে আমার C:\Users\カーン　ムハンマドダウドアリー\AppData\Local\Python\bin ফোল্ডারে এসব ইন্সটল করা আছে । সো পাথে এটা যোগ করতে হবে । 
```
C:\Users\カーン　ムハンマドダウドアリー>py -m ensurepip --upgrade
Looking in links: c:\Users\カーン~1\AppData\Local\Temp\tmpsv51kfj8
Requirement already satisfied: pip in .\AppData\Local\Python\pythoncore-3.14-64\Lib\site-packages (26.0.1)
```

Check:

```
python --version

```
2. Install Dependencies

```
pip install pyperclip keyboard

```
📜 Main Script: clipboard_logger.py

```
import pyperclip
import time
import keyboard
from datetime import datetime
import os

LOG_FILE = os.path.join(os.getcwd(), "cursor_chat_log.md")
last_text = ""

def get_timestamp():
    return datetime.now().strftime("%Y-%m-%d %H:%M:%S")

def format_entry(text, tag=None):
    entry = "\n\n---\n"
    entry += f"🕒 {get_timestamp()}\n"
    if tag:
        entry += f"🏷️ Tag: {tag}\n"
    entry += "\n```\n"
    entry += text.strip()
    entry += "\n```\n"
    return entry

def append_to_file(entry):
    with open(LOG_FILE, "a", encoding="utf-8") as f:
        f.write(entry)

def get_tag():
    print("\nEnter tag (optional): ")
    try:
        tag = input()
        return tag.strip() if tag else None
    except:
        return None

def manual_save():
    text = pyperclip.paste()
    tag = get_tag()
    entry = format_entry(text, tag)
    append_to_file(entry)
    print(f"[TAGGED SAVED] {get_timestamp()}")

keyboard.add_hotkey("ctrl+shift+s", manual_save)

print("📋 Clipboard Logger Running...")
print("➡️ Auto-save ON")
print("➡️ CTRL + SHIFT + S for tagging\n")

while True:
    try:
        text = pyperclip.paste()

        if text != last_text and len(text.strip()) > 20:
            entry = format_entry(text)
            append_to_file(entry)
            print(f"[AUTO SAVED] {get_timestamp()}")
            last_text = text

        time.sleep(1)

    except KeyboardInterrupt:
        print("\n🛑 Logger stopped.")
        break
```
▶️ Runner Script: run_logger.bat

```
@echo off
cd /d "C:\path\to\your\automation"
python clipboard_logger.py
pause

```
🧾 Example Output
---

```
🕒 2026-04-01 10:32:10
🏷️ Tag: Debug

```

Fixed pipeline issue in simulator trace...

🧠 Design Decisions
✔️ Why Clipboard?

Cursor API নেই → clipboard is the only reliable hook

✔️ Why Markdown?
Git-friendly
Human readable
Easy to search
✔️ Why Local?
Privacy
Works offline
No dependency
⚠️ Limitations
Manual copy required (Ctrl + C)
Hidden content capture করা যায় না
Clipboard overwrite issue থাকতে পারে
🔮 Future Improvements
📅 Daily log split
🔍 Search tool
🧠 Auto tagging (AI-based)
🖥️ GUI viewer
🏁 TL;DR

👉 Copy করলে auto log + hotkey দিলে tagging → full Cursor workflow automation (local only)
