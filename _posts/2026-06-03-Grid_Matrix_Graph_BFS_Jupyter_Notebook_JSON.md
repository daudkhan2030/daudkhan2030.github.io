---
title: "🌸 Grid, Matrix, Graph, BFS, Jupyter Notebook, JSON"
date: 2026-06-03
layout: single
categories:
    - notes
---
# Grid, Matrix, Graph, BFS, Jupyter Notebook, JSON — Personal Notes

## Grid vs Coordinate System

প্রথমে আমার সবচেয়ে বড় confusion ছিল Grid (Matrix) এবং Mathematical Coordinate System-এর মধ্যে।

### Mathematical Coordinate System

আমরা স্কুলে যেটা শিখি:

```text
        y+
         ↑
         |
---------+--------→ x+
         |
         |
```

এখানে:

* Origin = (0,0) কেন্দ্রবিন্দুতে
* x বাড়লে ডানে যাই
* y বাড়লে উপরে যাই

উদাহরণ:

```text
(2,2)
```

মানে ডানে ২ এবং উপরে ২।

---

### Grid / Matrix Coordinate System

Programming-এ Grid বা Matrix সাধারণত Top-Left থেকে শুরু হয়।

```text
(0,0) (0,1) (0,2)
(1,0) (1,1) (1,2)
(2,0) (2,1) (2,2)
```

এখানে:

* Row বাড়লে নিচে যাই
* Column বাড়লে ডানে যাই

অর্থাৎ:

```text
row + 1 = Down
row - 1 = Up

col + 1 = Right
col - 1 = Left
```

এ কারণেই BFS/DFS Grid Problems-এ:

```cpp
{0,1}   -> Right
{1,0}   -> Down
{0,-1}  -> Left
{-1,0}  -> Up
```

---

## Scalar, Vector, Matrix, Tensor

Machine Learning, Robotics, Computer Vision ইত্যাদিতে প্রায়ই এই terms দেখা যায়।

### Scalar

একটি মাত্র value।

```text
5
3.14
100
```

---

### Vector

একটি dimension-এর collection।

```text
[1, 2, 3]
```

বা

```cpp
vector<int>
```

---

### Matrix

Rows এবং Columns নিয়ে গঠিত 2D data।

```text
1 2 3
4 5 6
7 8 9
```

Programming-এ:

```cpp
vector<vector<int>>
```

---

### Tensor

Matrix-এর general form।

```text
0D -> Scalar
1D -> Vector
2D -> Matrix
3D+ -> Tensor
```

Example:

```text
Image Batch
=
Tensor
```

কারণ:

```text
Height × Width × Channel
```

---

## Graph vs Grid

### Grid

Fixed neighbour structure।

```text
□ □ □
□ □ □
□ □ □
```

প্রতিটি cell-এর neighbour সাধারণত:

```text
Up
Down
Left
Right
```

---

### Graph

Graph-এ arbitrary connection থাকতে পারে।

```text
A --- B
|     |
C --- D
```

এখানে neighbour structure predefined না।

---

## Number of Islands (LeetCode 200)

Problem:

```text
1 = Land
0 = Water
```

Connected Land = One Island

Goal:

```text
Count Islands
```

---

### Important Realization

BFS Island Count করে না।

BFS-এর কাজ:

```text
একটি Island-এর
সব connected land খুঁজে বের করা
```

---

### Mental Model

Outer Loop:

```text
Find a new unvisited land
```

যখন নতুন `1` পাওয়া যায়:

```cpp
islands++;
```

কারণ:

```text
নতুন Island শুরু হয়েছে
```

---

### BFS-এর কাজ

প্রথম land cell পাওয়ার পরে:

```text
Explore
Visit
Mark
```

Island-এর সব connected cell।

---

### Queue-এর Role

Queue store করে:

```text
Cells that still need exploration
```

Example:

```text
1 1
1 0
```

প্রথমে:

```text
queue = [(0,0)]
```

এরপর BFS neighbour দেখে:

```text
queue = [(0,1), (1,0)]
```

তারপর একে একে process করে।

---

### island++ কেন একবার?

কারণ:

```text
3 connected land
≠
3 islands
```

বরং:

```text
3 connected land
=
1 island
```

তাই:

```cpp
islands++;
```

শুধু নতুন island শুরু হলে।

BFS-এর ভিতরে নয়।

---

## BFS Direction Array

Common Pattern:

```cpp
int dirs[4][2] =
{
    {0,1},
    {1,0},
    {0,-1},
    {-1,0}
};
```

Meaning:

```text
Right
Down
Left
Up
```

Purpose:

```text
Check all neighbours
```

Current Cell-এর চারপাশে connected land আছে কিনা।

---

## Jupyter Notebook (.ipynb) vs Python Script (.py)

### .py File

Traditional Python Script।

```python
print("Hello")
```

Sequential execution।

---

### .ipynb File

Notebook।

Contains:

* Python Code
* Markdown
* Graphs
* Outputs
* Documentation

Cell-based execution।

Example:

```python
x = 10
```

অন্য Cell:

```python
print(x)
```

---

### Magic Commands

Notebook-এ:

```python
%timeit
```

বা

```python
!ls
```

ব্যবহার করা যায়।

এগুলো pure Python নয়।

---

### Internal Reality

`.ipynb`

আসলে:

```text
JSON File
```

যেখানে store হয়:

* Code Cells
* Outputs
* Metadata
* Markdown

---

## JSON Notes

JSON = JavaScript Object Notation

মূল ধারণা:

```text
Key-Value Pair
```

Example:

```json
{
  "name": "Daud",
  "age": 32
}
```

---

### Important Rules

Keys:

```json
"name"
```

Double Quotes ব্যবহার করতে হয়।

---

String Values:

```json
"Bangladesh"
```

Double Quotes ব্যবহার করতে হয়।

---

Numeric Values:

```json
32
```

Quotes প্রয়োজন নেই।

---

Boolean:

```json
true
false
```

Quotes প্রয়োজন নেই।

---

### Single Quotes

Invalid JSON:

```json
{
  'name': 'Daud'
}
```

কারণ JSON standard:

```text
Double Quotes Only
```

---

## Key Takeaways

* Grid এবং Mathematical Coordinate System এক জিনিস নয়।
* Grid Top-Left থেকে শুরু হয়।
* Row increase = Down।
* Column increase = Right।
* Scalar → Vector → Matrix → Tensor dimension অনুযায়ী evolve করে।
* Grid Problem-এ BFS connected component discover করে।
* Queue future exploration cells store করে।
* island++ শুধুমাত্র নতুন island শুরু হলে হয়।
* Jupyter Notebook code + markdown + output store করতে পারে।
* `.ipynb` internally JSON।
* JSON key/value format ব্যবহার করে এবং Double Quotes mandatory।
