# Master's Thesis — LaTeX Source

LaTeX source for the master's thesis
**"A Comparative Analysis of WebAssembly and Docker Containers for Microservice Architectures in Kubernetes"**
by Abdulaziz Musaev, Distributed Systems Engineering, TU Dresden.

The thesis compares a SpinKube / Wasmtime stack (WASI P2) against a Docker / runc baseline across four variants
(`wasm-rust`, `wasm-tinygo`, `docker-rust`, `docker-golang`) under two stateless HTTP workloads
(prime sieve and memory-bandwidth) on a single-node Kubernetes 1.34 cluster.

## Companion repositories

| Repository | Purpose |
| --- | --- |
| [thesis-infra-setup](https://github.com/abdulaziz7225/thesis-infra-setup) | Infrastructure-as-code for the experimental Kubernetes cluster used in the thesis. |
| [thesis-experiments](https://github.com/abdulaziz7225/thesis-experiments) | Benchmark implementations, load-test runners, and result data for the thesis. |
| **[master-thesis](https://github.com/abdulaziz7225/master-thesis)** (this repo) | The LaTeX source, figures, bibliography, and build files of the written thesis. |

## Repository layout

```text
wasm-vs-docker/
├── main.tex                  # Document entry point
├── settings/                 # Class config, metadata, acronym definitions
├── chapters/                 # Chapters 01–08
├── frontmatter/              # Abstract, acknowledgments
├── appendices/               # Reproducibility appendix
├── figures/                  # Compiled figures + TikZ sources
├── references.bib            # BibTeX bibliography
└── nsm-thesis.cls            # TU Dresden thesis class
```
