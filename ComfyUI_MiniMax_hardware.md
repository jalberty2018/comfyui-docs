# 💻 Hardware Requirements

MiniMax H3 model files are large and rely on ComfyUI offloading. Resolution, duration and concurrent model loading can increase both VRAM and system RAM requirements.

## High-VRAM profile

- Full `fl2va` and `ref2va` INT8 ConvRot diffusion models: about 34 GB each.
- Selected automatically when detected VRAM is above the default 36 GiB threshold.
- The workflow loads the diffusion model needed for its task; it does not require both diffusion models in VRAM simultaneously.

## Lower-VRAM profile

- Pruned `fl2va` and `ref2va` INT8 ConvRot diffusion models: about 21 GB each.
- Selected automatically at or below the default 36 GiB threshold.
- Sufficient system RAM and model offloading remain necessary.

## Shared models

- Qwen3-VL 32B INT8 ConvRot text encoder: about 27 GB on disk.
- Video VAE: about 5.2 GB on disk.
- Audio VAE: about 605 MB on disk.

Override automatic profile selection with the `VRAM_THRESHOLD` environment variable when testing a different balance between VRAM and offloading.
