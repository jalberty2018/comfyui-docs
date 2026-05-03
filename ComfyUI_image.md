[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image)

# Image inference with ComfyUI 

A streamlined and automated environment for running **ComfyUI** with **image/edit models**, optimized for use on RunPod

## Example ZIB-ZIT

![ZIB-ZIT](images/ai-generated-ZIB-ZIT.jpg)

## Example QWEN-EDIT 

![QWEN-EDIT-CAMERA](images/ai-generated-QWEN-EDIT-CAMERA.jpg)

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- Included workflows for **image generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attentions and GPU accelerations.
- Automatic selecting bf16 or fp8 models/workflows.
- Lora manager

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on runpod

- [👉 Templates](ComfyUI_image_deployment.md)

### Example is running Z-image on a RTX A4500

![Pod running on RTX A4500 ZIT ComfyUI](images/runpod_A4500_ZIB_ZIT.jpg)

### Example is running Z-image on a RTX A5000

![Pod running on RTX A4500 ZIT ComfyUI](images/runpod_A5000_ZIB_ZIT.jpg)

### Example is running Flux Klein 9B on a RTX A4500

![Pod running on RTX A4500 Flux Klein ComfyUI](images/runpod_FLUX_KLEIN.jpg)

### Example is running QWEN-EDIT fp8 on a RTX A5000

![Pod running on RTX A5000 QWEN-EDIT ComfyUI](images/runpod_A5000_QWEN-EDIT.jpg)