# Compatibility and evidence

Observed on 2026-09-08 for the protected 1.0.0 developer-preview candidate.
These are measured configurations, not a claim that every GPU model works.

| Configuration | Observed result |
| --- | --- |
| Windows x64 CPython 3.10–3.13 | Fresh offline installation, native imports, PySide6 GUI, CPU parallelism, cancellation, crash recovery, resource reuse and receipt validation passed on the existing test host |
| NVIDIA RTX 5070 Ti, CPython 3.10.11, PyTorch 2.11.0+cu128 | Actual CUDA execution, CPU/GPU overlap, physical GPU exclusivity, cancellation/recovery and transfer-inclusive output parity passed |
| Intel XPU | REFERENCE ONLY: interpreter and framework probing exists for future compatibility work; the current packaged desktop cannot schedule XPU; physical Intel hardware is NOT_CHECKED |
| AMD ROCm | REFERENCE ONLY: interpreter and framework probing exists for future compatibility work; the current packaged desktop cannot schedule ROCm; physical AMD hardware is NOT_CHECKED |
| Clean Windows / browser-download trust | NOT_CHECKED; fresh local virtual environments do not establish SmartScreen or Smart App Control acceptance |

Discovery, backend selection and successful device execution are different checks.
An installed package does not prove that its driver and hardware are compatible.
Explicit unavailable accelerator requests fail; CPU fallback must not be reported
as GPU execution. Automatic mode keeps ambiguous work on CPU.

PyRe does not convert ordinary Python loops into GPU code. Workloads must use
device-aware operations from a compatible framework. See the product website's
how-to and examples. Accelerator environments are separate from the base GUI
installation. The current Windows desktop supports CPU and NVIDIA CUDA execution.
Its Intel XPU and AMD ROCm probes are future-reference checks, not runnable
product backends. PyRe does not promise arbitrary OpenCL, DirectML, Vulkan or
Apple GPU compatibility.

See [measured benchmarks](benchmarks.md). Successful output parity is not a
universal speedup claim.
