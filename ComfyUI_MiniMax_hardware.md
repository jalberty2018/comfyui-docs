# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## Tested configurations

| Provisioning | GPU | Model | Purpose | Pod RAM | Tested output |
|---|---|---|---|---:|---|
| NVIDIA LVRAM | RTX 3090/4090 24 GB | Pruned INT8 ConvRot | Lowest cost and maximum compatibility | 50 GB | 0.9 MP, 15 seconds |
| NVIDIA HVRAM | L40S 48 GB | Full INT8 ConvRot | Quality and longer video | 80 GB | 0.9 MP, 20 seconds, 24 fps |
| Blackwell LVRAM | RTX 5090 32 GB | Pruned INT8 ConvRot | Compatible low-VRAM profile for Blackwell | 70 GB | 1.0 MP, 15 seconds, 24 fps |
| Blackwell HVRAM | RTX PRO 6000 96 GB | Full MXFP8 (FP8 scaled) | Maximum quality and speed | 70 GB | 2 MP, 15 seconds, 24 fps |

- Generation limits depend on resolution, duration, model selection and offloading. Allocate additional system RAM for larger workloads.
