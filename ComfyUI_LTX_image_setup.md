# ⚙️ Image setup

## Image

| Component | Version               |
|-----------|-----------------------|
| OS        | `Ubuntu 24.04 x86_64` |
| Python    | `3.12.x`              |
| PyTorch   | `2.10.0`              |
| Torchvision | `0.25.0`            |
| Torchaudio | `2.10.0`             |
| CUDA      | `12.8`                |
| cuDNN     | `9`                   |
| Triton    | `3.6.0`               |
| onnxruntime-gpu | `1.22.0`        |
| ComfyUI   | `0.33.1`              |
| Code Server | `latest`            |

## Wheels

| Package        | Version  |
|----------------|----------|
| flash_attn     | `2.8.4` |
| sageattention  | `2.2.0` |
| torch_generic_nms | `0.1` |
| llama-cpp-python | `0.3.34` |

## Optimized

|| Architecture | Compute Capability | Native Build Target | Examples |
|---|---:|---:|---|
| Ampere | 8.6 | `sm_86` | RTX 3090, RTX A5000, RTX A6000, A40 |
| Ada Lovelace | 8.9 | `sm_89` | RTX 4090, RTX 6000 Ada, L40, L40S |
| Blackwell | 12.0 | `sm_120` | RTX 5090, RTX PRO 6000 |

