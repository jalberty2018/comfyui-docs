# 💻 Hardware Requirements

## T2V-A14B or I2V-A14B (high/low) 

### **Recommended GPU**

- precision fp16
- video settings 1024x768 122 frames (ComfyUI-WanVideoWrapper offload 10)
- SVI v2 PRO: Long video's needs more RAM to avoid OOM (number of chunks are critical).

| GPU          | VRAM  | RAM ComfyUI-Native/ComfyUI-WanVideoWrapper |
|--------------------------|-------|-------------------------|
| L40S, RTX 6000 (Ada)       | 45Gb | 90Gb/50Gb           |

### **Recommended GPU** for SVI v2 PRO

- precision fp16
- video settings 1072x720 7 x 81 frames

| GPU          | VRAM  | RAM ComfyUI-Native/ComfyUI-WanVideoWrapper |
|--------------------------|-------|-------------------------|
| L40S         | 45Gb | minimum 95 Gb           |

### Possible GPU with limitations due to available ram on rupod

- precision fp16
- video settings 1024x768 97 frames (ComfyUI-WanVideoWrapper Offload 10)
- only possible with worflows based on ComfyUI-WanVideoWrapper (Included in pod)

| GPU       | VRAM  | RAM ComfyUI-WanVideoWrapper |
|--------------------------|-------|--------------|
| A40       | 45Gb | 45Gb |

### Animate

- precision fp16
- video settings 1024x768 77 chunks/Sampler

| Recommended GPU          | VRAM  | RAM   |
|--------------------------|-------|-------|
| L40S, RTX 6000 (Ada) | 40Gb | 105Gb | 

### SCAIL

- precision fp16
- Depends on length and size of video.

| Recommended GPU        | VRAM  | RAM    |
|------------------------|-------|--------|
| L40S, RTX 6000 (Ada)   | 40 GB | 105 GB |

## Storage

| Component        | Minimum                  |
|------------------|--------------------------|
| Volume Storage   | 90Gb (`/workspace`)      |
| Pod Storage      | 15Gb                     |