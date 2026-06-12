# 💻 Hardware Requirements

## T2V-A14B or I2V-A14B (high/low)

### **Recommended GPU**

- Precision: fp16.
- Video settings: 1024x768, 122 frames (ComfyUI-WanVideoWrapper offload 10).
- SVI v2 PRO: long videos need more RAM to avoid OOM; the number of chunks is critical.

| GPU          | VRAM  | RAM ComfyUI-Native/ComfyUI-WanVideoWrapper |
|--------------------------|-------|-------------------------|
| L40S, RTX 6000 (Ada)       | 45 GB | 90 GB / 50 GB           |

### **Recommended GPU** for SVI v2 PRO

- Precision: fp16.
- Video settings: 1072x720, 7 x 81 frames.

| GPU          | VRAM  | RAM ComfyUI-Native/ComfyUI-WanVideoWrapper |
|--------------------------|-------|-------------------------|
| L40S         | 45 GB | Minimum 95 GB           |

### Possible GPU with limitations due to available RAM on RunPod

- Precision: fp16.
- Video settings: 1024x768, 97 frames (ComfyUI-WanVideoWrapper offload 10).
- Only possible with workflows based on ComfyUI-WanVideoWrapper (included in the pod).

| GPU       | VRAM  | RAM ComfyUI-WanVideoWrapper |
|--------------------------|-------|--------------|
| A40       | 45 GB | 45 GB |

### Animate

- Precision: fp16.
- Video settings: 1024x768, 77 chunks/sampler.

| Recommended GPU          | VRAM  | RAM   |
|--------------------------|-------|-------|
| L40S, RTX 6000 (Ada) | 40 GB | 105 GB |

### SCAIL

- Precision: fp16.
- Depends on the length and size of the video.

| Recommended GPU        | VRAM  | RAM    |
|------------------------|-------|--------|
| L40S, RTX 6000 (Ada)   | 40 GB | 105 GB |

## Storage

| Component        | Minimum                  |
|------------------|--------------------------|
| Volume Storage   | 90 GB (`/workspace`)     |
| Pod Storage      | 15 GB                    |
