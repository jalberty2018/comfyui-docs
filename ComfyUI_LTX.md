[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-ltx)](https://hub.docker.com/r/ls250824/run-comfyui-ltx)

# LTX 2.3 inference with ComfyUI

A streamlined and automated environment for running **ComfyUI** with **LTX-2.3 video models**, optimized for use on RunPod.

## What to expect

These templates are intended for users who already want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens, and file management is helpful.

## When to use this template

Use this template for LTX 2.3 video generation, image-to-video, video-to-video, pose-transfer, camera-motion transfer, and audio/reference workflows.

## Example included workflows

### i2v

![Select number of frames, size, prompt and offload](images/ai-generated-LTX.jpg)

### vi2v pose transfer DWPose

![Select number of frames, size, prompt and offload](images/ai-generated-LTX-vi2v.jpg)

### vi2v pose transfer SDPose (Body Ratio Mapper)

![Select number of frames, size, prompt and offload](images/ai-generated-LTX-vi2v-sdpose.jpg)

## 🔧 Features

- Automatic model and LoRA provisioning via environment variables.
- [Kijai models without checkpoints](https://huggingface.co/Kijai/LTX2.3_comfy).
- Included workflows for **video generation** and **enhancement** using pre-installed custom nodes.
- Compatible with high-performance NVIDIA GPUs (CUDA 12.8).
- Compiled attention and GPU acceleration.
- Automatic selection of bf16 or fp8 models/workflows.
- Latent preview enabled for both samplers.
- Included workflows based on [RuneXX](https://huggingface.co/RuneXX/LTX-2.3-Workflows).
- LoRA Manager.

## 🔧 Built-in **authentication**
  
- ComfyUI
- Code Server
- Hugging Face API
- CivitAI API

## 📦 Deployment on RunPod

- [👉 Templates](ComfyUI_LTX_deployment.md)

## 📘 Tutorial

- [Specific for this template](ComfyUI_LTX_tutorial.md)

### Pod running on L40S bf16

![Pod running on L40S ComfyUI](images/runpod_L40S_LTX.jpeg)

### Pod running on RTX 6000 Ada bf16

![Pod running on RTX 6000 Ada ComfyUI](images/runpod_6000Ada_LTX.jpeg)

### Pod running on RTX A5000 fp8

![Pod running on RTX A5000 ComfyUI](images/runpod_A5000_LTX.jpeg)

### Pod running on RTX 4090 fp8

![Pod running on RTX 4090 ComfyUI](images/runpod_RTX4090_LTX.jpeg)
