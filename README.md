# Python BST & LRU

**Two data structures, made visible: binary search trees and least-recently-used caching.**

A notebook-based Python coursework project exploring ordered lookup, search paths, cache recency, and eviction. The BST notebooks draw tree structures with NetworkX and Matplotlib; the LRU notebook prints the cache's most-recently-used to least-recently-used ordering after each demonstration step.

Developed for a Data Structure class at the National University of Management.

## Explore the notebooks

| Notebook | What it demonstrates | Status |
| --- | --- | --- |
| [bst.ipynb](bst.ipynb) | A small keyword BST with highlighted search paths | Source reviewed; not executed in this refresh |
| [bst copy.ipynb](bst%20copy.ipynb) | CSV loading, cleaning, BST insertion, and full-tree plotting | Large-data experiment; start with a small input |
| [lru_cache_project.ipynb](lru_cache_project.ipynb) | Dictionary + doubly linked list cache with recency promotion and eviction | Source reviewed; not executed in this refresh |
| [performance_test.ipynb](performance_test.ipynb) | Intended comparison with a list-based cache | Currently blocked; see below |

## Binary search tree

Each node stores a key and left/right children. Insertion places smaller keys to the left and larger keys to the right; duplicate keys are ignored. `search_path` returns the visited keys and whether the target was found.

The visualisation marks visited nodes in orange, a found target in green, and other nodes in light blue. The small demo shuffles its keyword list with a fixed random seed before insertion.

**This is not a self-balancing tree.** Shuffling insertion order does not guarantee balance, and no AVL or red-black rebalancing is implemented. Recursive insertion and graph construction can become problematic for deep trees.

### CSV experiment

The separately named `bst copy.ipynb` reads [data.csv](data.csv), selecting the `word` column by default. The file also contains a `count` column, but the configured indexer uses words as keys rather than frequency-weighted nodes.

The loader drops missing values, converts remaining values to strings, and removes duplicates. If the requested column is absent, it falls back to the first column. If the file is missing, it attempts to create a small sample CSV at that path.

The supplied dataset is large, and the notebook attempts to draw the entire tree. **Use a small working dataset first.** A successful data load is not evidence that full-tree rendering will be readable or practical. The dataset's original source and redistribution terms are not documented in the supplied repository.

## LRU cache

`LRUCache` combines a dictionary for key lookup with a doubly linked list for recency ordering. Dummy head and tail nodes simplify list updates.

- `get(key)` returns the value and promotes a hit to the most-recently-used position; a miss returns `-1`.
- `put(key, value)` inserts or replaces an entry at the front.
- Exceeding capacity evicts the entry immediately before the tail.
- `display()` prints the current MRU-to-LRU order; it is a textual view, not an interactive graphical tool.

The included capacity-three demonstration inserts keys 1, 2, and 3, accesses key 1, then inserts key 4 to evict key 2.

The implementation is designed around constant-size linked-list updates and dictionary lookup, not a measured performance guarantee. It does not validate capacity, distinguish a stored `-1` from a miss, or provide thread-safety controls. Its annotations describe integer values, while the demonstration stores strings.

## Run locally

Use Python 3 with a notebook environment. The export records Python 3.13.9 in notebook metadata, but that is not a verified minimum version or a pinned environment.

Suggested installation for the imports used by these notebooks and a JupyterLab interface:

```sh
python -m pip install jupyterlab networkx matplotlib pandas
python -m jupyterlab
```

These packages are not version-pinned, and this setup was not executed during the documentation refresh.

1. Start with `bst.ipynb` or `lru_cache_project.ipynb`.
2. Use a separate kernel, or restart it, when switching notebooks: both define a class named `Node`.
3. For the CSV experiment, make the repository root the working directory and inspect `CSV_FILE_PATH` and `CSV_COLUMN_NAME` before running. Use a small input first.
4. Do not treat the performance notebook as runnable until its blockers are fixed.

## Benchmark status

The supplied benchmark does **not** establish a speedup:

- It imports `LRUCache` from `lru_cache_project`, but the repository contains a notebook with that name, not an importable `.py` module. Its saved output records `ModuleNotFoundError`.
- `SlowCache.get` refers to an undefined `value` instead of the tuple value `v` on a hit.
- The workload uses 50,000 loop iterations, each with one `put` and one `get`; it is not 50,000 individual cache calls.
- Keys cycle over the same range as capacity, so this workload does not exercise eviction after filling the cache.
- The final speedup statement is hard-coded rather than derived from measured results.

These issues are documented, not repaired by this documentation-only package. No timing results or performance claims are published here. See [implementation notes](docs/implementation-notes.md).

## Contributing and security

Read [CONTRIBUTING.md](CONTRIBUTING.md) for focused changes and verification expectations, and [SECURITY.md](SECURITY.md) for notebook and data-handling concerns.

## Licence

No licence file is included in the supplied repository. This refresh does not assign a licence or establish redistribution rights for the dataset. The owner should choose code licensing explicitly and establish the data's provenance separately.
