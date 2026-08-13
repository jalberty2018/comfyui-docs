# 💻 Hardware Requirements

The LTX 2.3 values below are tested minimums for the listed settings. The LTX 2.5 values are conservative provisioning targets based on the official model
sizes and ComfyUI offloading; they are not universal benchmarked minimums.
Higher resolution, longer videos, larger batches, concurrent model loading, or
less offloading can require more VRAM and system RAM.

## LTX-2.5

### GPU and system RAM

| Configuration | Typical GPU | VRAM target | System RAM | Guidance |
|---------------|-------------|-------------|------------|----------|
| int8-convrot transformer and encoder | RTX 3090, RTX 4090, RTX 5090 | 24 GB minimum; 32 GB preferred | 64 GB minimum; 80 GB recommended | LVRAM model set; use ComfyUI offloading. |
| int8-convrot transformer with BF16 encoder | L40S, RTX A6000, RTX 6000 Ada | 48 GB | 80 GB minimum; 96 GB recommended | HVRAM model set used by an L40S with the supplied threshold. |
| int8-convrot transformer with BF16 encoder | A100/H100 80 GB, RTX PRO 6000 96 GB | 80 GB or more | 96 GB minimum; 128 GB recommended | HVRAM model set with more headroom for larger workflows. |

The templates do not provision a BF16 transformer. The public profile uses the
distilled int8-convrot transformer without the distilled LoRA. The private
profile uses the dev int8-convrot transformer with the distilled LoRA.

### RunPod VRAM selection

The supplied LTX 2.5 profiles use `VRAM_THRESHOLD=40`. The startup script
selects the HVRAM model set when detected VRAM is **greater than** 40 GB. An
L40S therefore receives the int8-convrot transformer with the Heretic BF16
text encoder. GPUs at or below the threshold receive the same transformer
precision with the Heretic int8-convrot text encoder.

### Storage

| Selected chain | Model storage guidance |
|----------------|------------------------|
| Public distilled int8-convrot with Heretic encoder | Allow at least 60 GB |
| Private dev int8-convrot, distilled LoRA, and Heretic encoder | Allow at least 65 GB |

Use at least 120 GB of persistent `/workspace` storage for one complete profile,
ComfyUI, custom nodes, and a modest amount of output. Increase this for long or
high-resolution videos because generated frames, previews, and cached files can
quickly consume the remaining space.

## LTX 2.3

The example screenshots in the overview page document successful LTX 2.3 runs
with these GPU classes on RunPod.

### BF16

- Precision: bf16.
- Video settings: 1920x1088, 20 sec, 24 fps.

| GPU          | Min VRAM  | Min RAM |
|--------------------------|-------|-------------------------|
| L40S / RTX 6000 Ada | 45 GB | 60 GB           |

### FP8

- Precision: fp8 mixed.
- Video settings: 1280x736, 20 sec, 24 fps.

| GPU          | Min VRAM  | Min RAM |
|--------------------------|-------|-------------------------|
| RTX A5000 / RTX 4090 | 24 GB | 50 GB           |
