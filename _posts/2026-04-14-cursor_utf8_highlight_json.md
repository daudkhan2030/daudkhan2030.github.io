---
title: "🏮 Search Colour Highlight & Gibberish Japanese to Original UTF-8"
date: 2026-04-14
layout: single
categories:
  - notes
---

- কার্সরে সার্চ করলে অ্যাশ কালারে হাইলাইট হয় রেজাল্ট যেটা আসলে খুবই ইনকনভিনিয়েন্ট । এজন্য নিচের স্টেপ ফলো করলাম ।
1. Press:

```
Ctrl + Shift + P
```

2. Type:

```
Preferences: Open User Settings (JSON)
```
👉 NOT just “Open Settings (JSON)”
👉 Make sure it says **User Settings**

```
{
  "workbench.colorCustomizations": {
    "editor.findMatchBackground": "#ffff00cc",
    "editor.findMatchHighlightBackground": "#ff000099",
    "editor.findRangeHighlightBackground": "#00ffcc66",
    "editor.findMatchBorder": "#000000",
    "editor.selectionHighlight": true,
    "editor.occurrencesHighlight": "on"
  }
}
```
<img width="1130" height="442" alt="image" src="https://github.com/user-attachments/assets/d8cebce0-b652-49ac-889a-8a4b676b82af" />

# Gibberish Japanese to Original

<aside>
💡

কার্সর থেকে জাপানিজ জিব্রিশ দেখাচ্ছিল । সেটাকে কারেক্ট করার জন্য নিচের ইন্সট্রাকশন । 

</aside>

- Ctrl + Shift + P —→           Preferences: Open User Settings (JSON)
- Ctrl + Shift + P —→           Preferences: Open Default Settings (JSON)

<img width="1179" height="185" alt="image" src="https://github.com/user-attachments/assets/06bc41b4-fd01-438e-9ddc-f4c5ac86f873" />

- settings.json        &       defaultSettings.json

<img width="1445" height="575" alt="image" src="https://github.com/user-attachments/assets/17ba4bc1-173a-4dda-98f1-a59c316a9b5b" />

- files.autoGuessEncoding": false এই কোড true হিসেবে সেট করতে হবে । সাথে utf8 ও সেট করতে হবে যাতে জাপানিজ ভেঙ্গে না যায় ।
- 

```
{
  "workbench.colorCustomizations": {
    "editor.findMatchBackground": "#ffbf0061",
    "editor.findMatchHighlightBackground": "#ff000099",
    "editor.findRangeHighlightBackground": "#00ffcc66",
    "editor.findMatchBorder": "#000000"
  },

  "editor.selectionHighlight": true,
  "editor.occurrencesHighlight": "multiFile",

  "files.autoGuessEncoding": true,
  "files.encoding": "utf8"
}
```

- সমস্য হলো যে ফাইলে আমরা রিড করতে পারি কিন্তু রাইট না সেজন্য এজেন্টকে দিবো occurrencesHighlight সেটা রাইট করতে । সেজন্য occurrencesHighlight এটা মার্ক করে add এ ক্লিক করে true সেট করতে বলি।
- 

<img width="969" height="553" alt="image" src="https://github.com/user-attachments/assets/9ced7dd0-8acf-47f4-acbd-999578408ccf" />

- আবার আমার হাইলাইটেড টেক্সট অনেক ব্রাইট থাকায় আমি বুঝতে পারছিলাম না সেজন্য এই ফাইলে নিজে নিজে কালার চুজ করা যায় । অনেক ইজি।




