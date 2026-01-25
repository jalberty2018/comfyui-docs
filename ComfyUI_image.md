[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image)

# Image (t2i, ti2i) inference with ComfyUI 

![Pod running on RTX A4500 native comfyUI](images/runpod_ZIT.jpg)

A streamlined and automated environment for running **ComfyUI** with **image/edit models**, optimized for use on RunPod.io

Ecample is running Z-image Turbo on a RTX A4500 on Runpod

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- Supports advanced workflows for **image generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attentions and GPU accelerations.
- Automatic selecting bf16 or fp8 models/workflows if supported, view [hardware requirements](ComfyUI_image_hardware.md) for possible GPU's

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on runpod

- [👉 Templates](ComfyUI_image_deployment.md)
