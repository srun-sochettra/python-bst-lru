# Advanced Data Structures with Python

This project contains high-performance implementations and visual demonstrations of fundamental and advanced data structures. Developed as part of the **Advanced Data Structures with Python** course at the **National University of Management (NUM)**, these notebooks focus on both algorithmic efficiency and practical visualization.

## 🚀 Project Overview

The repository is structured around key data structures, providing clean Python implementations, detailed visualizations, and performance benchmarking.

### 1. Binary Search Tree (BST) Indexer
*   **File:** `bst.ipynb`
*   **Description:** Implements a standard Binary Search Tree optimized for indexing string-based data.
*   **Key Features:**
    *   **Visualization:** Uses `networkx` and `matplotlib` to render the tree structure dynamically.
    *   **Search Path Highlighting:** Visualizes the exact path taken through the tree during a search operation, highlighting visited nodes.
    *   **CS Keyword Demo:** Pre-loaded with over 20+ computer science terms to demonstrate tree balancing and retrieval.

### 2. Optimized LRU Cache
*   **File:** `lru_cache_project.ipynb`
*   **Description:** A custom implementation of a **Least Recently Used (LRU) Cache** designed for $O(1)$ time complexity for both `get` and `put` operations.
*   **Key Features:**
    *   **Hybrid Architecture:** Combines a **Hash Map** (for fast lookup) with a **Doubly Linked List** (for efficient ordering).
    *   **Real-time Visualization:** Includes a "Visualizer" tool that prints the cache state (MRU to LRU) after every operation.
    *   **Eviction Logic:** Demonstrates how the least recently used items are automatically evicted when capacity is exceeded.

### 3. Performance Benchmarking
*   **File:** `performance_test.ipynb`
*   **Description:** A "Performance Showdown" notebook that compares the optimized data structures against naive implementations.
*   **Tests Included:**
    *   **Optimized vs. Naive LRU:** Compares the $O(1)$ Hash+DLL approach against an $O(N)$ List-based approach over 50,000 operations.
    *   **Results:** Highlights the significant speed advantages of using appropriate data structures for large-scale data handling.

## 🛠️ Setup & Requirements

To run these notebooks, you will need Python 3 and the following libraries:

```bash
pip install networkx matplotlib
```

Once installed, you can launch the notebooks using Jupyter Lab or VS Code:

1.  Open `bst.ipynb` to see tree visualizations.
2.  Open `lru_cache_project.ipynb` to see the cache in action.
3.  Open `performance_test.ipynb` to run the speed benchmarks.

## 📊 Data
*   `data.csv`: A sample dataset used for testing larger-scale indexing and retrieval operations.

---
*Created for the Data Structure Class at the National University of Management.*
