# Security policy

This repository contains local Python notebooks and a CSV dataset, not a hosted service. It does not establish continuous monitoring, supported release lines, a response deadline, or a security certification.

## Notebook and data boundaries

Notebook code executes with the permissions of its Python process. Review cells before running them and use a suitable local environment. The CSV notebook reads a configured path and can create a sample CSV there if the file is missing.

Large inputs and full-tree rendering can consume substantial resources. The recursive BST implementation and plotting routines are not designed as hardened services for untrusted workloads. Do not expose them as a public processing endpoint without a separate review.

Avoid committing credentials, personal information, local paths, or sensitive notebook outputs. The dataset's original source and redistribution terms are not established by the supplied files; do not assume it is cleared for every reuse.

## Reporting concerns

For non-sensitive defects, open an issue with the affected notebook/cell, Python and package versions, minimal input, and reproduction steps. Redact private paths and data.

For sensitive concerns, request a private contact from the repository owner without publishing exploit details or private information. No dedicated reporting email or private reporting feature is confirmed by the supplied repository.

The benchmark defects documented in the README are correctness and reproducibility issues; this policy does not claim they are security vulnerabilities.
