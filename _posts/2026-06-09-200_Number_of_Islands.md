---
title: "🌸 LeetCode Problem 200: Number of Islands - A Deep Dive into DFS"
date: 2026-06-09
layout: single
categories:
  - engineering
---

এই প্রজেক্টটিতে আমি LeetCode-এর জনপ্রিয় প্রবলেম "Number of Islands" সমাধান করেছি DFS (Depth-First Search) অ্যালগরিদম ব্যবহার করে। নিচে আমার কোড এবং এর পেছনের লজিক বিস্তারিত আলোচনা করা হলো।

The Approach: Why DFS?
এই প্রবলেমটি সল্ভ করার জন্য আমি Recursive DFS ব্যবহার করেছি। BFS-এর তুলনায় DFS কোডটি অনেক concise এবং ক্লিন, কারণ এখানে আলাদা করে কোনো queue ম্যানেজ করার প্রয়োজন পড়ে না। সিস্টেমের নিজস্ব Call Stack-ই এই কাজটি হ্যান্ডেল করে।

Code Breakdown (Module by Module)1. The dfs Function (The Engine)এই ফাংশনটি মূলত একটি নির্দিষ্ট দ্বীপের (Island) সমস্ত কানেক্টেড অংশকে খুঁজে বের করে এবং সেগুলোকে "sink" করে দেয়।

```cpp
void dfs(vector<vector<char>>& grid, int i, int j) {
    // Boundary checks & Base case
    if (i < 0 || i >= grid.size() || j < 0 || j >= grid[0].size() || grid[i][j] == '0')
        return;

    grid[i][j] = '0'; // Marking as visited (Sinking the island)

    // Recursive calls for 4 directions
    dfs(grid, i + 1, j);
    dfs(grid, i - 1, j);
    dfs(grid, i, j + 1);
    dfs(grid, i, j - 1);
}
```

- Boundary Checks: প্রথমেই চেক করা হয় ইনডেক্সগুলো গ্রিডের ভেতরে আছে কি না (i < 0, i >= grid.size()) এবং সেলটি ল্যান্ড ('1') কি না। যদি '0' হয় বা সীমানার বাইরে হয়, তাহলে আমরা রিটার্ন করি।
- Marking Visited: grid[i][j] = '0' এর মাধ্যমে আমরা visited সেলগুলোকে মার্ক করে দিই, যাতে করে এগুলো বারবার গোনা না হয়।
- Recursion: এখানে আমরা dfs(i+1, j) এর মতো করে recursively চারদিকে সার্চ করি। এখানেই DFS তার সৌন্দর্য দেখায়—কোনো আলাদা queue ছাড়াই এটি পুরো দ্বীপটি ঘুরে আসে।

  2. The numIslands Function (The Controller)এটি মেইন লুপ যা পুরো গ্রিডটি স্ক্যান করে।

  ```cpp
  int numIslands(vector<vector<char>>& grid) {
    int islands = 0;
    for (int i = 0; i < grid.size(); i++) {
        for (int j = 0; j < grid[0].size(); j++) {
            if (grid[i][j] == '1') {
                islands++; // New island found!
                dfs(grid, i, j); // Sink the whole island
            }
        }
    }
    return islands;
  ```

  DFS vs. BFS: My Learning
  আমাদের আলোচনায় আমরা জেনেছি কেন DFS এবং BFS আলাদা:
  - Queue Management: BFS ব্যবহার করলে আমাদের স্পষ্টভাবে একটি std::queue ম্যানেজ করতে হতো, যা কোডকে লেন্থি করে তোলে। DFS-এ এই কাজটি ব্যাকগ্রাউন্ডে System Call Stack করে দেয়, তাই কোড ছোট থাকে।
  - Directional Search: BFS-এ dr, dc, nr, nc এর মতো এক্সট্রা স্টাফ ব্যবহার করে মুভমেন্ট ক্যালকুলেট করতে হয়। DFS-এ আমরা সরাসরি প্যারামিটার হিসেবে i+1, i-1 পাস করতে পারি, যা অনেক বেশি স্বাচ্ছন্দ্যের।
  - Efficiency: যদিও DFS অনেক বেশি concise, তবে মনে রাখতে হবে—খুব বড় গ্রিডের ক্ষেত্রে গভীর রিকার্সনের কারণে Stack Overflow হওয়ার ঝুঁকি থাকে। সেদিক থেকে BFS মেমোরির দিক দিয়ে কিছুটা বেশি সেফ (Safe)।
  
Complexity Analysis
Time Complexity: O(M X N), যেখানে $M$ হলো গ্রিডের সারি (rows) এবং $N$ হলো কলাম (columns)। কারণ আমরা প্রতিটি সেল বড়জোর একবারই ভিজিট করছি।
Space Complexity: O(M X N), রিকার্সিভ স্ট্যাকের (recursive stack) জন্য worst-case scenario-তে এতখানি মেমোরি প্রয়োজন হতে পারে।

  এই প্রজেক্টটি করার মাধ্যমে আমি Grid Traversal এবং Recursion-এর বেসিক কনসেপ্টগুলোকে আরও ভালোভাবে আয়ত্ত করতে পেরেছি। ধন্যবাদ!
