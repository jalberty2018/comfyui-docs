[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image)

# Image (t2i, ti2i) inference with ComfyUI 

![Pod running on RTX A4500 native comfyUI](images/runpod_ZIT.jpg)

A streamlined and automated environment for running **ComfyUI** with **image/edit models**, optimized for use on RunPod.io

Ecample is running Z-image Turbo on a RTX A4500 on Runpod

## 🔧 Features

- Automatic model and LoRA downloads via environment variables or Lora manager.
- Supports advanced workflows for **image generation** and **enhancement** using pre-installed custom nodes
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8)

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on runpod

- [👉 Templates](ComfyUI_image_deployment.md)
