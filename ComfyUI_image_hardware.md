# 💻 Hardware

## Hardware requirements

| Model           | Tested GPU          | Min VRAM | Min RAM |
|-----------------|---------------------|----------|---------|
| Z-Image Turbo   | RTX A4500, RTX A5000 | 20 GB    | 50 GB   |
| ERNIE-Image     | RTX A4500 | 20 GB    | 50 GB   |
| Flux.2 Klein    | RTX A4500    | 20 GB    | 50 GB   |
| Flux.2 Dev bp16 | RTX A6000 ada | 44 GB    | 80 GB   |
| Flux.2 Dev fp8  | RTX 3090    | 24 GB    | 50 GB   |
| Qwen image bf16       | RTX A6000  | 44 GB    | 65 GB   |
| Qwen image fp8        | RTX A5000 , RTX 3090 | 24 GB    | 45 GB   |
| Qwen image edit bf16  | RTX A6000 | 44 GB    | 65 GB   |
| Qwen image edit fp8   | RTX A5000 , RTX 3090  | 24 GB    | 45 GB   |

## Volume storage requirements

| Model | Minimum                    |
|-------|----------------------------|
| ZI    | 50 GB (`/workspace`)       |
| ERNIE | 50 GB (`/workspace`)       |
| Flux bf16 | 90 GB (`/workspace`)       |
| Flux fp8 | 75 GB (`/workspace`)       |
| Qwen  | 70 GB (`/workspace`)       |

## Pod storage requirements

| Model | Minimum                    |
|-------|----------------------------|
| —     | 15 GB                      |