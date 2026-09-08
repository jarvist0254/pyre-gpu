# Measured CPU/CUDA results

Observed 2026-09-08 for the protected PyRe 1.0.0 developer-preview candidate.

**CPU was faster in these small transfer-inclusive trials.** This validates device execution and numerical parity; it is not a universal GPU speedup claim. Measure representative workloads before choosing a lane.

- CPU: AMD Ryzen 7 7700; one PyTorch CPU thread.
- GPU: NVIDIA GeForce RTX 5070 Ti; driver 591.86 measured separately.
- Windows x64; CPython 3.10.11; PyTorch 2.11.0+cu128; CUDA build 12.8.
- Workload: dense square matrix multiplication C = A @ B, shape256×256, float32.
- Seed1729; CPU generator uniform[0,1) minus0.5; one warmup and five measured repetitions per trial.
- Autograd disabled through inputs without gradients; TF32 off; highest float32 matrix precision.
- Full output comparison: abs(cuda − cpu) ≤0.0001 +0.0001×abs(cpu), every65,536 elements.
- GPU elapsed time includes initial synchronization, host-to-device transfer, kernel, device-to-host transfer and completion synchronization. CPU time covers CPU matrix multiplication. Input generation and the validation comparison are outside the measured interval.

## Timing distributions

Milliseconds; rounded for display. Two independent measured runs used the same seeded inputs.

| Trial / lane | Min | Median | Mean | p10 | p90 | Max |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| A / CPU | 0.311000 | 0.393800 | 0.425860 | 0.319160 | 0.575300 | 0.690300 |
| A / CUDA with transfers | 0.465900 | 0.516300 | 0.521080 | 0.476740 | 0.568740 | 0.583300 |
| B / CPU | 0.311200 | 0.333900 | 0.349960 | 0.312680 | 0.399820 | 0.419500 |
| B / CUDA with transfers | 0.445400 | 0.478500 | 0.490580 | 0.453800 | 0.534680 | 0.548200 |

## Individual samples

| Trial/sample | CPU ms | GPU H2D ms | GPU kernel ms | GPU D2H ms | GPU total ms | Max absolute error | Parity |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| A/1 | 0.690300 | 0.236300 | 0.173600 | 0.133400 | 0.583300 | 2.38418579e-06 | PASS |
| A/2 | 0.331400 | 0.217500 | 0.176400 | 0.082600 | 0.516300 | 2.38418579e-06 | PASS |
| A/3 | 0.393800 | 0.182200 | 0.154100 | 0.117700 | 0.493000 | 2.38418579e-06 | PASS |
| A/4 | 0.311000 | 0.199200 | 0.162800 | 0.070500 | 0.465900 | 2.38418579e-06 | PASS |
| A/5 | 0.402800 | 0.193200 | 0.189100 | 0.130900 | 0.546900 | 2.38418579e-06 | PASS |
| B/1 | 0.419500 | 0.197900 | 0.174000 | 0.102100 | 0.514400 | 2.38418579e-06 | PASS |
| B/2 | 0.311200 | 0.199400 | 0.156800 | 0.054200 | 0.445400 | 2.38418579e-06 | PASS |
| B/3 | 0.370300 | 0.179500 | 0.166700 | 0.085400 | 0.466400 | 2.38418579e-06 | PASS |
| B/4 | 0.314900 | 0.199200 | 0.165400 | 0.078400 | 0.478500 | 2.38418579e-06 | PASS |
| B/5 | 0.333900 | 0.240400 | 0.186300 | 0.079700 | 0.548200 | 2.38418579e-06 | PASS |

All ten samples passed complete output parity. Kernel time alone is not end-to-end acceleration. This test does not certify other devices, larger inputs or every library operation.

Candidate artifact SHA-256: `228d218c6ace273b700049b1ca2b8feaa0a5e20180b1b45800a72a822b0af4a3`. Application files remain private and are not distributed by this repository.
