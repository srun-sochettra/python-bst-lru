# Implementation notes

These notes describe the supplied source. They are not results from executing the notebooks.

## BST notebooks

Both BST notebooks define their own `Node` and `BST` classes. The node stores `key`, `left`, and `right`. Insertion is recursive; search follows child pointers iteratively while recording the path. Equal keys do not create new nodes.

Graph construction recursively visits the tree, adding directed edges and plotting positions. `visualize` clears the previous graph and positions, rebuilds them, and calls NetworkX drawing followed by Matplotlib display. It draws the whole tree even when highlighting one search path.

The keyword notebook uses a fixed-seed shuffled list. The CSV notebook separately implements loading and cleaning, defaults to `data.csv` and its `word` column, and searches for `rtcw` in its demonstration. Neither notebook implements self-balancing, deletion, or a persistent on-disk index.

The CSV loader's null removal and deduplication are not a general text-normalisation pipeline. It does not explicitly trim whitespace or normalise letter case. Its missing-file branch writes sample data, so inspect the configured path before execution.

The two notebooks' class definitions are separate implementations, not a shared importable library. Reusing a kernel across them can overwrite the global `Node` name, so restart or separate kernels when switching demonstrations.

## LRU notebook

The dictionary maps keys to nodes. The doubly linked list uses sentinel head/tail nodes, with the most-recently-used entry immediately after the head and the least-recently-used immediately before the tail.

A hit unlinks and re-adds its node at the front. An update removes the old node and creates a replacement at the front. An insertion beyond capacity removes the tail-adjacent entry from both the list and dictionary. Display walks the list and prints its ordering.

The code does not validate capacity or implement concurrency control. The `-1` miss sentinel is ambiguous if `-1` is stored as a value. Type annotations and string-valued examples are not aligned. These are documented limitations, not fixes included in this refresh.

## Benchmark blockers

`performance_test.ipynb` imports `LRUCache` from `lru_cache_project`, but no corresponding Python module is included. The saved notebook output records a missing-module error. Merely running the other notebook does not create an importable module for this import.

In the list-based cache's hit branch, the loop binds `(k, v)` but reinsertion uses `value`, which is undefined in that method. This is a second source-level blocker after the import problem.

The default workload is 50,000 iterations, each performing a put and get. Keys use `i % 100`, and both caches have capacity 100. It therefore focuses on repeated insert/update and immediate access rather than capacity-driven eviction. The final conclusion is printed unconditionally, not computed from timing comparisons.

A useful future repair should establish a shared import path, correct the baseline, check both implementations against the same expected results, and report actual timing with its environment and workload. No such repair or measurement is included here.
