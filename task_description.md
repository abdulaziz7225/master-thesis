# Task Description — Content for Signed Form

## Header fields

- **Name:** Abdulaziz Musaev
- **Matriculation number:** 5170092
- **Title:** A Comparative Analysis of WebAssembly and Docker Containers for Microservice Architectures in Kubernetes

## Objectives of work

### Introduction

Containerized deployment on Kubernetes, with Docker-style OCI images executed under runc, has become the de facto execution model for cloud-native microservice architectures. The model is mature and ergonomic. However, each container instance still carries a baseline cost in image footprint, cold-start latency, and per-instance memory consumption. These costs become visible at high deployment density or under rapid scale-out.

WebAssembly (Wasm), together with the WebAssembly System Interface (WASI), has recently been proposed as a complementary server-side execution model for the same class of workloads. A growing Kubernetes-oriented ecosystem — including Fermyon Spin and SpinKube, wasmCloud, KWasm, Krustlet, and runwasi-based containerd shims, on top of runtimes such as Wasmtime and WasmEdge — promises substantially smaller artefacts, faster startup, and a different isolation boundary than conventional containers. Whether this maturing toolchain is, today, a viable alternative to Docker for production microservices is an open question that the existing literature provides only limited empirical coverage of.

The objective of this thesis is to provide a controlled, reproducible empirical comparison of Docker- and WebAssembly-based microservices in a Kubernetes cluster, scoped to clearly defined workloads and quality attributes, and to derive evidence-based recommendations for practitioners considering server-side Wasm.

### Concept

The work will follow an experimental, measurement-driven methodology grounded in a single comparison matrix. Four functionally equivalent services are to be implemented and deployed to the same Kubernetes cluster, combining the runtime axis (Docker vs. WebAssembly) with the language-family axis (Rust vs. Go-family). The four variants are a Rust service compiled to Wasm (wasm-rust), a TinyGo service compiled to Wasm (wasm-tinygo), a Rust service packaged as a Docker/OCI image (docker-rust), and a Go service packaged as a Docker/OCI image (docker-golang). All four variants will expose the same HTTP API and implement the same algorithms, so that observed differences are attributable to the runtime and language/runtime combination rather than to application logic.

The planned Wasm integration is Fermyon Spin together with SpinKube, which builds on the Wasmtime runtime and a containerd Wasm shim. This is not the only option. The survey portion of the thesis will also discuss alternative Kubernetes integrations such as wasmCloud, KWasm, and Krustlet, as well as alternative runtimes such as WasmEdge. The final choice will be justified before the experiments are run.

Four complementary HTTP workloads will be exercised: CPU-bound (prime-sieve), memory-bound (memory-bandwidth), I/O-bound (HTTP fan-out against an in-cluster delay-injecting backend), and serialization + allocator (JSON parse / sort / re-serialise). Each workload runs under both resource-constrained and unconstrained configurations, with load applied by a representative HTTP load generator. Each variant will be evaluated quantitatively along a small set of metrics covering OCI image size, binary artefact size, cold-start and warm-start latency, sustained throughput, end-to-end request-latency percentiles, and runtime CPU and memory footprint. It will also be evaluated qualitatively along a developer-experience assessment covering toolchain setup, dependency compatibility, Kubernetes integration, and debugging and observability.

The thesis is expected to close with a synthesis of the quantitative and qualitative findings and a recommendation on when server-side Wasm in Kubernetes is, and is not, a justified alternative to Docker today. The work will be accompanied by a publicly released artefact bundle to support independent reproduction.

## Focus of work

Survey of WebAssembly as a server-side execution environment in Kubernetes. The survey covers the Wasm and WASI specifications, the Component Model, candidate runtimes (e.g. Wasmtime, WasmEdge), and Kubernetes integrations (e.g. Fermyon Spin / SpinKube, wasmCloud, KWasm, Krustlet, runwasi-based shims). It is contrasted with the conventional Docker / OCI / runc deployment workflow.

Design and implementation of four functionally equivalent HTTP microservices — wasm-rust, wasm-tinygo, docker-rust, and docker-golang — exposing identical APIs and implementing identical algorithmic logic across the runtime and language-family axes. The four-variant design is replicated across four examples (prime-sieve, memory-bandwidth, http-fanout, json-roundtrip) covering the CPU-bound, memory-bound, I/O-bound, and serialization + allocator workload classes respectively.

Setup of a reproducible Kubernetes test environment, including the build, image, and deployment automation required to run the Docker and WebAssembly variants side by side.

Implementation of four HTTP benchmark workloads — CPU-bound (prime-sieve), memory-bound (memory-bandwidth), I/O-bound (HTTP fan-out), and serialization + allocator (JSON round-trip) — driven by a representative HTTP load generator under both resource-constrained and unconstrained configurations.

Quantitative evaluation of the four variants along OCI image size, binary artefact size, cold- and warm-start latency, sustained throughput under concurrent HTTP load, end-to-end request-latency percentiles, and CPU and memory footprint at idle and under load. This is complemented by a qualitative developer-experience assessment covering toolchain setup, dependency compatibility, Kubernetes integration, and debugging and observability.

Synthesis of the quantitative and qualitative findings into evidence-based recommendations for adopting server-side WebAssembly in Kubernetes-based microservice architectures. The work is accompanied by a publicly released artefact bundle to support independent reproduction.

## Footer fields (to be completed by hand before signing)

- **Referee:** _________________________
- **Supervisor:** _________________________
- **Issued on:** _________________________
- **Due date for submission:** _________________________
- **Supervising professor:** Prof. Dr. Christof Fetzer *(pre-printed on the form)*
