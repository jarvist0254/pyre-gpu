# PyRe GPU by JE Horizon

PyRe plans and supervises Python workloads on CPU and NVIDIA CUDA in the current
packaged desktop. It does not convert arbitrary CPU code into GPU code.

[Product and release status](https://pyre.jehorizon.com/)

This repository contains public product documentation and issue reporting.
Application source and downloads are distributed separately by JE Horizon.

## Developer preview

The Windows developer preview is undergoing final release verification.
Purchase and application downloads are not open yet. Protected Windows x64
CPython 3.10–3.13 installs, the PySide6 desktop, CPU concurrency, cancellation and
crash recovery passed on the test host. NVIDIA CUDA execution and output parity
passed on an RTX 5070 Ti. Intel XPU and AMD ROCm probes are reference paths for
future compatibility work; the current packaged desktop cannot schedule those
backends, and physical Intel and AMD hardware remains NOT_CHECKED.

The introductory price is **$29 USD one time**, for perpetual use of the purchased
application and compatible v1.x updates. There is no recurring subscription.

## What PyRe does

- Queues scripts through a durable local controller and preserves job identities.
- Runs admitted CPU work concurrently and reserves each selected NVIDIA GPU
  for one active job at a time.
- Checks physical memory, commit, VRAM, disk and supported thermal observations.
- Shows actual backend selection, captured output, outcomes and receipts in a
  PySide6 desktop interface.
- Keeps admitted work running when the window disconnects, with recovery and
  cancellation evidence tracked by the controller.

See [installation](docs/installation.md), [compatibility](docs/compatibility.md)
and [support](SUPPORT.md). [Measured results](docs/benchmarks.md) identify the
workload, hardware, software and transfer-inclusive timings. They are not a
promise that all workloads become faster.

PyRe's compiled implementation raises the barrier to inspecting its core source.
It is not a guarantee against reverse engineering. Windows trust observations
and compatibility are specific to tested releases and environments.

Copyright JE Horizon. Application use is governed by the purchased license.
