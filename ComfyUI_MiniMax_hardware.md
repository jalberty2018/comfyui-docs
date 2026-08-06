# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## Hardware tested

### MiniMax H3 full INT8 ConvRot

- video settings 0.9 MP 20 sec 24fps

| GPU          | VRAM  | RAM |
|--------------------------|-------|-------------------------|
| L40S | 45Gb | 80Gb           |

### MiniMax H3 pruned NVFP4

- video settings 0.4 MP 15sec 24fps

| GPU          | VRAM  | RAM |
|--------------------------|-------|-------------------------|
| RTX 5090 | 32Gb | 70Gb           |
