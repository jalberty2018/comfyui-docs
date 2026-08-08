# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## Hardware tested

| Profile | GPU | VRAM | System RAM | Tested workload |
|---|---|---:|---:|---|
| Full INT8 ConvRot with Turbo LoRA | L40S | 45 GB | 80 GB | 0.9 MP, 20 seconds, 24 fps |
| Pruned NVFP4 with Turbo LoRA | RTX 5090 | 32 GB | 70 GB | 0.4 MP, 15 seconds, 24 fps |
| Pruned fp8 scaled with Turbo LoRA | RTX PRO 6000 | 62 GB | 70 GB | 1 MP, 30 seconds, 24 fps |