# ⚙️ Image setup

## Image

| Component | Version              |
|-----------|----------------------|
| OS        | `Ubuntu 22.04 x86_64` |
| Python    | `3.11.x`             |
| PyTorch   | `2.9.1`              |
| CUDA      | `12.8`               |
| Triton    | `3.5.1`              |
| onnxruntime-gpu | `1.22.x`       |
| ComfyUI   | `0.31.0`             |
| Code Server | `latest`           |

## Wheels

| Package        | Version  |
|----------------|----------|
| flash_attn     | `2.8.3` |
| sageattention  | `2.2.0` |
| torch_generic_nms | `0.1` |
| llama-cpp-python | `0.3.16` |

## Optimized

|| Architecture | Compute Capability | Native Build Target | Examples |
|---|---:|---:|---|
| Ampere | 8.6 | `sm_86` | RTX 3090, RTX A5000, RTX A6000, A40 |
| Ada Lovelace | 8.9 | `sm_89` | RTX 4090, RTX 6000 Ada, L40, L40S |
