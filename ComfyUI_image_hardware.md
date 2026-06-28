# 💻 Hardware Requirements

These are tested minimums for the listed templates. Larger resolutions, larger batches, or extra custom nodes can require more VRAM and RAM.
The example screenshots in the overview page document successful runs with these GPU classes on RunPod.

## Image Models

| Model           | Working GPU          | Min VRAM | Min RAM |
|-----------------|---------------------|----------|---------|
| Z-Image Turbo   | RTX 3090, RTX A5000 | 20 GB    | 50 GB   |
| ERNIE-Image     | RTX A4500 | 20 GB    | 50 GB   |
| Krea-2  bf16   | RTX A5000 |  24 GB    | 65  GB   |
| Krea-2  fp8   | RTX A4500 |  20 GB    | 65  GB   |
| FLUX.2 Klein    | RTX A4500    | 20 GB    | 50 GB   |
| FLUX.2 Dev bf16 | RTX 6000 Ada | 44 GB    | 80 GB   |
| FLUX.2 Dev fp8  | RTX 3090    | 24 GB    | 50 GB   |
| JoyAI-image-edit bf16 | L40S | 43 GB    | 60 GB   |
| Qwen Image bf16       | RTX A6000  | 44 GB    | 65 GB   |
| Qwen Image fp8        | RTX A5000, RTX 3090 | 24 GB    | 45 GB   |
| Qwen Image Edit bf16  | RTX A5000 | 24 GB    | 65 GB   |
| Qwen Image Edit fp8   | RTX A5000, RTX 3090  | 24 GB    | 45 GB   |

## Volume Storage Requirements

| Model | Minimum                    |
|-------|----------------------------|
| Z-Image | 50 GB (`/workspace`)       |
| ERNIE | 50 GB (`/workspace`)       |
| Krea-2 bf16 | 90 GB (`/workspace`)       |
| Krea-2 fp8 | 60 GB (`/workspace`)       |
| FLUX bf16 | 90 GB (`/workspace`)       |
| FLUX fp8 | 75 GB (`/workspace`)       |
| JoyAI-image-edit bf16 | 70 GB (`/workspace`)       |
| Qwen Image | 70 GB (`/workspace`)       |

## Pod Storage Requirements

| Model | Minimum                    |
|-------|----------------------------|
| —     | 15 GB                      |
