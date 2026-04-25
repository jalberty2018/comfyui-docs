[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-wan2)](https://hub.docker.com/r/ls250824/run-comfyui-wan2)

# WAN 2.x inference with ComfyUI

![Select number frames, size , prompt and offload](images/ai-generated-WAN.jpg)

A streamlined and automated environment for running **ComfyUI** with **WAN 2.x video models**, optimized for use on RunPod

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- Included workflows for **video generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attentions and GPU accelerations.
- Latent preview enabled for samplers.
- Lora manager

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on runpod

- [👉 Templates](ComfyUI_WAN_deployment.md)

### Pod running on L40S

![Pod running on L40S native comfyUI](images/runpod.jpg)

### Pod running on A40

![Pod running on A40 comfyUI wanwrapper](images/runpod_A40_wrapper.jpg)

