---
title: "Engineering Test Post"
date: 2026-03-05
categories:
  - engineering
tags:
  - oop
  - abstraction
layout: single
---

aliasing বলতে মূলত বোঝায় — একই object / memory location-কে একাধিক reference বা pointer দিয়ে access করা।

সহজভাবে বললে:
একই জিনিসকে যদি একাধিক নাম বা handle দিয়ে ধরা যায়, তখন সেটাকে alias বলে।

উদাহরণ (pointer দিয়ে)
int x = 10;

int* p1 = &x;
int* p2 = &x;

এখানে:

p1 → x কে point করছে

p2 → x কেই point করছে

অর্থাৎ একই memory address দুইটা pointer ব্যবহার করছে।

তাই এখানে p1 এবং p2 হলো alias of x।

Reference দিয়েও alias হয়
int x = 10;

int& r1 = x;
int& r2 = x;

এখানে

r1 = x এর alias

r2 = x এর alias

কারণ দুটোই same memory location access করছে।

Important nuance

aliasing শুধু multiple pointer হলেই হয় না।
multiple access path to same memory হলেই alias হয়।

মানে:

pointer + pointer

reference + reference

pointer + reference

সব ক্ষেত্রেই হতে পারে।

Example (pointer + reference alias)
int x = 5;

int* p = &x;
int& r = x;

*p = 20;

std::cout << r; // 20

কারণ p এবং r দুটোই same object x access করছে।

এক লাইনে সংজ্ঞা

Aliasing = যখন একাধিক variable / pointer / reference একই memory location-কে refer করে।
