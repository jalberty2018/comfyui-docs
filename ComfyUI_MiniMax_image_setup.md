# ⚙️ Image setup

## Image

| Component | Version              |
|-----------|----------------------|
| OS        | `Ubuntu 24.04 x86_64` |
| Python    | `3.12.x`             |
| PyTorch   | `2.10.0`             |
| Torchvision | `0.25.0`           |
| Torchaudio | `2.10.0`            |
| CUDA      | `12.8`               |
| cuDNN     | `9`                  |
| Triton    | `3.6.0`              |
| onnxruntime-gpu | `1.22.0`     |
| ComfyUI | `0.30.0` |
| CodeServer | `latest`          |

## Wheels

| Package        | Version  |
|----------------|----------|
| flash_attn     | `2.8.3`    |
| sageattention  |  `2.2.0`   |
| torch_generic_nms | `0.1` |

## Optimised

| Family | Compute Capability | Processor example | SM |
|------------|---------|--------|-----------|
| Ampere  | 8.6 |  A40   | sm_86 |
| Ada Lovelace | 8.9 | L40S  | sm_89 |