[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image)

# Image inference with ComfyUI

A streamlined and automated environment for running **ComfyUI** with **image/edit models**, optimized for use on RunPod.

## Example ZIB-ZIT

![ZIB-ZIT](images/ai-generated-ZIB-ZIT.jpg)

## Example FLUX-Klein control/target image generation

![FLUX-Klein](images/ai-generated-FLUX-KLEIN.jpg)

## Example Qwen-Image-Edit multiple angles

![QWEN-EDIT-CAMERA](images/ai-generated-QWEN-EDIT-CAMERA.jpg)

## Example FLUX.2 Dev multiple angles

![FLUX2-CAMERA](images/ai-generated-FLUX2-CAMERA.jpg)

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- Included workflows for **image generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attention and GPU acceleration.
- Automatic selection of bf16 or fp8 models/workflows.
- LoRA Manager.

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on RunPod

- [👉 Templates](ComfyUI_image_deployment.md)

### Example running Z-Image on an RTX A4500

![Pod running on RTX A4500 ZIT ComfyUI](images/runpod_A4500_ZIB_ZIT.jpg)

### Example running Z-Image on an RTX A5000

![Pod running on RTX A5000 ZIT ComfyUI](images/runpod_A5000_ZIB_ZIT.jpg)

### Example running Z-Image on an RTX 4000 Ada

![Pod running on RTX 4000 Ada ZIT ComfyUI](images/runpod_4000ADA_ZIB_ZIT.jpg)

### Example running Z-Image on an RTX 3090

![Pod running on RTX 3090 ZIT ComfyUI](images/runpod_3090_ZIB_ZIT.jpg)

### Example running FLUX Klein 9B on an RTX A4500

![Pod running on RTX A4500 Flux Klein ComfyUI](images/runpod_FLUX_KLEIN.jpg)

### Example running Qwen-Image-Edit fp8 on an RTX A5000

![Pod running on RTX A5000 QWEN-EDIT fp8 ComfyUI](images/runpod_A5000_QWEN-EDIT.jpg)

### Example running Qwen-Image-Edit bf16 on an A40

![Pod running on A40 QWEN-EDIT bf16 ComfyUI](images/runpod_A40_QWEN-EDIT.jpg)

### Example running FLUX.2 Dev bf16 on an L40S

![Pod running on L40S Flux.2 Dev bf16 ComfyUI](images/runpod_L40S_FLUX_2.jpg)

### Example running FLUX.2 Dev fp8 on an RTX A5000 (slow)

![Pod running on A5000 Flux.2 Dev fp8 ComfyUI](images/runpod_A5000_FLUX_2.jpg)
