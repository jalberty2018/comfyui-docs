# 💻 Hardware Requirements

| Model           | Tested GPU          | Min VRAM | Min RAM |
|-----------------|---------------------|----------|---------|
| Z-Image Turbo   | RTX A5000, A4500    | 20 GB    | 50 GB   |
| Flux.2 Dev      | RTX A6000           | 44 GB    | 50 GB   |
| Qwen image bf16       | RTX A6000           | 44 GB    | 65 GB   |
| Qwen image fp8        | RTX A4090          | 24 GB    | 50 GB   |
| Qwen image edit       | RTX A6000           | 44 GB    | 65 GB   |

| Component       | Model | Minimum                    |
|-----------------|-------|----------------------------|
| Volume Storage  | ZIT   | 50 GB (`/workspace`)       |
| Volume Storage  | Flux  | 90 GB (`/workspace`)       |
| Volume Storage  | Qwen  | 70 GB (`/workspace`)       |
| Pod Storage     | —     | 15 GB                      |