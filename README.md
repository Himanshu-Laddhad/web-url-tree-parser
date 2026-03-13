# HW2 – Web URL Tree Structure Parser

**Course:** MGTA 590 – Web Data Analytics | Purdue University
**Skills:** Python · Nested Dictionaries · URL Parsing · Tree Data Structures · File I/O

---

## Overview

This project parses a flat list of URL paths and reconstructs them as a hierarchical tree using nested Python dictionaries — mirroring how a real website's navigation structure is organized. It demonstrates an elegant algorithmic approach to building multi-level data structures dynamically from string input.

---

## Problem

Given a CSV file of URL paths like:

```
home/faculty
home/faculty/bios
home/research/publications
home/about
```

Build a nested dictionary tree that reflects the website's structure:

```python
{
  'home': {
    'faculty': {
      'bios': {}
    },
    'research': {
      'publications': {}
    },
    'about': {}
  }
}
```

---

## Solution Approach

Instead of using deeply nested `if` statements (which become unmanageable beyond 3–4 levels), the solution uses a **double `for` loop with a moving pointer** — making it scalable to any depth:

1. Read all paths from `links_hw2.csv` and strip whitespace.
2. For each path, split on `"/"` to get a list of path segments.
3. Use a `node` pointer starting at the root dictionary.
4. Walk segment by segment: if a key doesn't exist, create an empty dict; advance the pointer one level deeper.
5. Repeat for every path in the input list.

This approach handles arbitrarily deep URL hierarchies with a fixed, concise loop structure.

---

## Files

| File | Description |
|---|---|
| `laddhad_himanshu_hw2.ipynb` | Main notebook with solution and explanations |
| `links_hw2.csv` | Input file containing URL paths (one per line) |

---

## Key Concepts Demonstrated

| Concept | Description |
|---|---|
| Nested dictionary construction | Building multi-level dicts dynamically |
| Pointer/reference manipulation | Moving `node` reference through dict levels |
| String splitting & parsing | Decomposing URL paths into segments |
| File I/O | Reading CSV input with `open()` and `.readlines()` |
| Scalable algorithm design | O(n × depth) solution vs. brittle if-else trees |

---

## Tech Stack

- **Language:** Python 3
- **Environment:** Jupyter Notebook
- **Libraries:** None (pure Python standard library)

---

## How to Run

1. Ensure `links_hw2.csv` is in the same directory as the notebook.
2. Open `laddhad_himanshu_hw2.ipynb` in Jupyter.
3. Run all cells (`Kernel → Restart & Run All`).
4. The final cell displays the full nested tree dictionary.

---

## Sample Output

```python
{
  'home': {
    'faculty': {'bios': {}, 'research': {}},
    'about': {},
    'contact': {}
  },
  'events': {
    'upcoming': {},
    'archive': {'2023': {}, '2024': {}}
  }
}
```
