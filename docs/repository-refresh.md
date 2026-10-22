# Repository refresh

## Recommended identity

- Current slug: `bst-n-lru`.
- Recommended slug: `python-bst-lru`.
- Display name: **Python BST & LRU**.
- Suggested description: **Python notebooks exploring binary search trees, search-path visualisation, and LRU caching with a dictionary and doubly linked list.**
- Suggested topics: `python`, `data-structures`, `binary-search-tree`, `lru-cache`, `jupyter-notebook`, `networkx`, `matplotlib`.

The recommendation replaces the informal connector with the implementation language while retaining the two defining data structures. No GitHub rename, description update, topic change, or remote update was performed.

## Apply this package

Extract the ZIP into the existing repository root. Replace README.md and add the other documentation files. Keep all existing notebooks, data.csv, local configuration, and Git history. This is a documentation overlay, not a complete repository replacement.

If adopting the name, rename the remote repository through its settings and update existing clones to the new clone URL. The archive does not perform that action.

Notebook filenames are deliberately unchanged. In particular, `bst copy.ipynb` is documented as the CSV experiment rather than silently deleted or renamed. Fixing the benchmark and reorganising source code are separate implementation tasks.

## Editorial changes

The README now explains what the code actually demonstrates, distinguishes local notebook experiments from a reusable library, includes the pandas dependency for the CSV notebook, and records the benchmark blockers. It removes unsupported balancing and speedup claims.

Security and contributing guides are proportional to local notebooks. No generic conduct policy, CI configuration, licence, performance result, or dependency pin was invented.

## Verification boundary

The four notebook JSON documents were parsed, and their code-cell source was inspected and syntax-parsed. The supplied README and CSV header were inspected; no claim of auditing every dataset value is made. Relative documentation links, file references, and ZIP integrity were checked.

Syntax parsing does not execute imports or notebook cells. No package installation, notebook execution, plotting, benchmark, or automated behavioural test was performed. Existing saved outputs are historical artefacts, not fresh verification.

The overlay excludes notebooks and data, preserving the implementation and dataset. To revert, restore the previous README and remove the newly added documentation files using version control.
