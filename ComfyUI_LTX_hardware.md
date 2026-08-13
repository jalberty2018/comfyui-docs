# 💻 Hardware Requirements

The LTX 2.3 values below are tested minimums for the listed settings. The LTX 2.5 values are conservative provisioning targets based on the official model
sizes and ComfyUI offloading; they are not universal benchmarked minimums.
Higher resolution, longer videos, larger batches, concurrent model loading, or
less offloading can require more VRAM and system RAM.

## LTX-2.5

### GPU and system RAM

| Configuration | Typical GPU | VRAM target | System RAM | Guidance |
|---------------|-------------|-------------|------------|----------|
| int8-convrot transformer and encoder | RTX 3090, RTX 4090, RTX 5090 | 24 GB minimum; 32 GB preferred | 64 GB minimum; 80 GB recommended | Recommended consumer-GPU profile; use ComfyUI offloading. |
| int8-convrot transformer with BF16 encoder | L40S, RTX A6000, RTX 6000 Ada | 48 GB | 80 GB minimum; 96 GB recommended | Useful when BF16 prompt conditioning is preferred; allow additional loading and offloading time. |
| BF16 transformer and encoder | A100/H100 80 GB, RTX PRO 6000 96 GB | 80 GB or more recommended | 96 GB minimum; 128 GB recommended | Best headroom for the full BF16 profile and larger workflows. |

An L40S can experiment with the BF16 transformer using aggressive offloading,
but the int8-convrot transformer is the safer default when generation
resolution, duration, or two-stage processing increases activation memory.

### RunPod VRAM selection

The supplied LTX 2.5 profiles use `VRAM_THRESHOLD=48`. The startup script
selects BF16 only when detected VRAM is **greater than** 48 GB. GPUs with 48 GB
or less, including an L40S, receive the int8-convrot transformer. The Heretic
BF16 and int8-convrot profiles fix the text-encoder precision independently of
this transformer selection.

### Storage

| Selected chain | Approximate model storage |
|----------------|---------------------------|
| BF16 transformer and BF16 encoder | 82 GB |
| int8-convrot transformer and official int8-convrot encoder | 51 GB |
| int8-convrot transformer and Heretic int8-convrot encoder | 48 GB |
| Optional Gemma 4 prompt enhancer | Additional 10.3 GB |

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
