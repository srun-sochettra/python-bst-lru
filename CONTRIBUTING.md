# Contributing

Keep this project focused on understandable data-structure implementations and honest demonstrations. Read the [README](README.md) and [implementation notes](docs/implementation-notes.md) first.

## Working with notebooks

- Keep changes small and preserve unrelated cells, outputs, and metadata.
- Use separate kernels for notebooks that define their own `Node` class.
- Restart the kernel and run relevant cells in order before reporting a successful execution.
- Distinguish saved output from a fresh run. Clear stale results when changing the code that produced them.
- Do not add private data, credentials, machine-specific paths, or large generated plots to commits.
- Check the CSV path before execution: the loader can create a sample file when the path does not exist.

## Verification expectations

For BST changes, check insertion, duplicate handling, found/missing searches, visited paths, and skewed input. Do not claim balancing without an implemented balancing algorithm and supporting tests.

For LRU changes, check misses, hit promotion, replacement, eviction, list ordering, and capacity edge cases. Explain any change to the `-1` miss convention or accepted value types.

For benchmark changes, first repair the missing module import and undefined variable. Check correctness before timing. Describe the workload, count iterations separately from cache calls, include eviction if relevant, and derive conclusions from results rather than hard-coded text.

No automated test suite or pinned environment is included in the supplied export. Report the Python/package versions, cells executed, results, and remaining gaps. Do not label a source review or syntax check as a successful notebook run.

## Pull requests

Explain the problem, focused change, verification, and compatibility implications. Include small, readable visual examples for plotting changes. Keep large-data experiments separate from quick correctness checks.

Sensitive concerns should follow [SECURITY.md](SECURITY.md). These guidelines do not establish a project licence or dataset reuse permission.
