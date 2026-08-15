# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## Tested configurations

| Provisioning profile | GPU | GPU memory | Pod RAM | Tested output |
|---|---|---:|---:|---|
| Standard NVIDIA LVRAM — Pruned INT8 ConvRot with Turbo LoRA | RTX 3090 | 24 GB |50 GB | 0.9 MP, 15 seconds |
| Standard NVIDIA HVRAM — Full INT8 ConvRot with Turbo LoRA | L40S | 48 GB | 80 GB | 0.9 MP, 20 seconds, 24 fps |
| Blackwell LVRAM — Pruned NVFP4 with Turbo LoRA | RTX 5090 | 32 GB | 70 GB | 0.4 MP, 15 seconds, 24 fps |
| Blackwell HVRAM — Full MXFP8 (FP8 scaled) with Turbo LoRA | RTX PRO 6000 Blackwell | 96 GB | 70 GB | 2 MP, 15 seconds, 24 fps |

- Generation limits depend on resolution, duration, model selection and offloading. Allocate additional system RAM for larger workloads.
