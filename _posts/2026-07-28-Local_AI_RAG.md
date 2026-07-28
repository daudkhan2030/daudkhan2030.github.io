---
title: "👛👀 Local AI RAG System Setup (Windows) using Open WebUI + Ollama"
date: 2026-07-28
layout: single
categories:
  - engineering
---
# 🧠 Local AI RAG System Setup (Windows) | Open WebUI + Ollama + Qwen3

সম্প্রতি আমি আমার Windows Laptop-এ একটি **Fully Local AI RAG (Retrieval-Augmented Generation)** System তৈরি করেছি, যাতে নিজের Japanese PDF Documents আপলোড করে Local AI-কে প্রশ্ন করা যায় এবং সেই Documents-এর ভিত্তিতে উত্তর পাওয়া যায়।

সবচেয়ে ভালো বিষয় হলো—

- ✅ সম্পূর্ণ Local
- ✅ Free
- ✅ Open Source
- ✅ কোনো API Key লাগেনি
- ✅ কোনো ChatGPT Subscription লাগেনি
- ✅ নিজের Documents-এর উপর AI Question Answering

---

# আমি যেসব Technology ব্যবহার করেছি

```text
Windows 11
Docker Desktop
WSL2 (Windows Subsystem for Linux)
Open WebUI
Ollama
Qwen3:8B (Local LLM)
Sentence Transformers (Default Embedding)
```

---

# Overall Architecture

```text
Japanese PDF
     |
     ▼
Open WebUI
     |
     ▼
Embedding
     |
     ▼
Vector Database
     |
     ▼
Qwen3:8B (Ollama)
     |
     ▼
Answer based on my documents
```

---

# Step 1 : Docker Desktop Install

প্রথমে Windows-এ Docker Desktop Install করেছি।

---

# Step 2 : WSL2 Install

Docker চালানোর জন্য WSL2 Install করেছি।

PowerShell (Administrator)

```powershell
wsl --install
```

Installation শেষ হওয়ার পর

```text
Restart Windows
```

---

# Step 3 : Docker চালু করা

Docker Desktop Open করেছি এবং নিশ্চিত করেছি যে

```text
Engine Running
```

দেখাচ্ছে।

---

# Step 4 : Open WebUI Download ও Run

PowerShell-এ নিচের Command চালিয়েছি।

```powershell
docker run -d `
-p 3000:8080 `
-v open-webui:/app/backend/data `
--name open-webui `
--restart always `
ghcr.io/open-webui/open-webui:main
```

Docker Image Download হওয়ার পর Container Run হয়েছে।

---

# Step 5 : Browser থেকে Open WebUI Open

```text
http://127.0.0.1:3000
```

---

# Step 6 : Local AI Model ব্যবহার

Open WebUI-এর সাথে Ollama ব্যবহার করেছি।

Model হিসেবে

```text
qwen3:8b
```

ব্যবহার করেছি।

---

# Step 7 : নিজের Knowledge Base তৈরি

```text
Knowledge

↓

Create Knowledge
```

তারপর একটি নতুন Collection তৈরি করেছি।

উদাহরণ

```text
RAGDoc
```

---

# Step 8 : Japanese PDF Upload

Knowledge Collection-এর ভিতরে নিজের Japanese PDF Upload করেছি।

উদাহরণ

```text
職務要件・昇格基準定義書.pdf

sateimanual1.pdf
```

---

# Step 9 : AI-কে প্রশ্ন করা

Documents Upload করার পরে Chat-এ ফিরে গিয়ে প্রশ্ন করেছি।

Example

```text
Summarize this document.

Explain the requirements.

What are the promotion criteria?

Answer in English.
```

AI Uploaded Documents Search করে সেই অনুযায়ী উত্তর দেয়।

---

# ব্যবহৃত Command গুলো

## WSL Install

```powershell
wsl --install
```

---

## Docker Container Run

```powershell
docker run -d `
-p 3000:8080 `
-v open-webui:/app/backend/data `
--name open-webui `
--restart always `
ghcr.io/open-webui/open-webui:main
```

---

## Running Container Check

```powershell
docker ps
```

---

## Installed Model Check

```powershell
ollama ps
```

---

## Model Information

```powershell
ollama show qwen3:8b
```

---

# Final Workflow

```text
Japanese PDF
     |
     ▼
  Upload
     |
     ▼
Knowledge Collection
     |
     ▼
Embedding
     |
     ▼
Vector Search
     |
     ▼
Qwen3:8B
     |
     ▼
Answer generated from my uploaded documents
```

---

# Outcome

এই Setup-এর মাধ্যমে আমি Local Machine-এই নিজের Japanese Documents-এর উপর AI Question Answering System তৈরি করতে পেরেছি।

যেহেতু সবকিছু Local Machine-এ চলছে, তাই কোনো Cloud API বা Paid AI Service ব্যবহার করতে হয়নি। নিজের Documents Upload করে English-এ প্রশ্ন করলে AI সেই Documents-এর Context অনুযায়ী উত্তর দিতে পারে।

এটি Technical Documentation, Manuals, Requirements, Design Documents এবং Knowledge Management-এর জন্য একটি কার্যকর Local RAG Solution।
