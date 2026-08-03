# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## Hardware tested

### MiniMax H3 INT8 Convrot

- video settings 1 MP 15 sec 24fps

| GPU          | VRAM  | RAM |
|--------------------------|-------|-------------------------|
| L40S | 45Gb | 80Gb           |

### MiniMax H3 fp8 pruned

- video settings 1 MP 15sec 24fps

| GPU          | VRAM  | RAM |
|--------------------------|-------|-------------------------|
| RTX 5090 | 32Gb | 70Gb           |
