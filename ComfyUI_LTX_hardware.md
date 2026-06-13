# 💻 Hardware Requirements

These are tested minimums for the listed settings. Higher resolution, longer videos, larger batches, or less offloading can require more VRAM and RAM.
The example screenshots in the overview page document successful runs with these GPU classes on RunPod.

## LTX 2.3 bf16

- Precision: bf16.
- Video settings: 1920x1088, 20 sec, 24 fps.

| GPU          | Min VRAM  | Min RAM |
|--------------------------|-------|-------------------------|
| L40S / RTX 6000 Ada | 45 GB | 60 GB           |

### LTX 2.3 fp8

- Precision: fp8 mixed.
- Video settings: 1280x736, 20 sec, 24 fps.

| GPU          | Min VRAM  | Min RAM |
|--------------------------|-------|-------------------------|
| RTX A5000 / RTX 4090 | 24 GB | 50 GB           |
