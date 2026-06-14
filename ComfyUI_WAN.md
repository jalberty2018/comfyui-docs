[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-wan2)](https://hub.docker.com/r/ls250824/run-comfyui-wan2)

# WAN 2.x inference with ComfyUI

![Select number of frames, size, prompt and offload](images/ai-generated-WAN.jpg)

A streamlined and automated environment for running **ComfyUI** with **WAN 2.x video models**, optimized for use on RunPod.

## What to expect

These templates are intended for users who already want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens, and file management is helpful.

## When to use this template

Use this template for WAN 2.x video generation, image-to-video, animation, long-video, SVI, and SCAIL workflows.

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- Included workflows for **video generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attention and GPU acceleration.
- Latent preview enabled for samplers.
- LoRA Manager.

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on RunPod

- [👉 Templates](ComfyUI_WAN_deployment.md)

## 📘 Tutorial

- [Specific for these templates](ComfyUI_WAN_tutorial.md)

### Pod running on L40S

![Pod running on L40S native ComfyUI](images/runpod.jpg)

### Pod running on A40

![Pod running on A40 ComfyUI WanVideoWrapper](images/runpod_A40_wrapper.jpg)

