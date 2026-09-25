# ⚙️ Image setup

## Image

| Component | Version              |
|-----------|----------------------|
| OS        | `Ubuntu 24.04 x86_64` |
| Python    | `3.12.x`             |
| PyTorch   | `2.12.1+cu130`             |
| Torchvision | `0.27.1+cu130`           |
| Torchaudio | `2.11.0+cu130`            |
| CUDA      | `13.0`               |
| cuDNN     | `9`                  |
| Triton    | `3.7.1`              |
| onnxruntime-gpu | `1.22.*`     |
| ComfyUI | `0.37.1` |
| Native llama.cpp | `b11115` |
| CodeServer | `latest`          |

## Wheels

| Package        | Version  |
|----------------|----------|
| flash_attn     | `2.8.4`    |
| sageattention  |  `2.2.0`   |
| torch_generic_nms | `0.1` |
| llama-cpp-python | `0.3.35` |

## Optimised

| Architecture | Compute Capability | Native Build Target | Examples |
|---|---:|---:|---|
| Ampere | 8.6 | `sm_86` | RTX 3090, RTX A5000, RTX A6000, A40 |
| Ada Lovelace | 8.9 | `sm_89` | RTX 4090, RTX 6000 Ada, L40, L40S |
| Blackwell | 12.0 | `sm_120` | RTX 5090, RTX PRO 6000 |
