[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-minimax)](https://hub.docker.com/r/ls250824/run-comfyui-minimax)

# MiniMax inference with ComfyUI

A streamlined and automated environment for running **ComfyUI** with **MiniMax H3 video and native-audio generation**, optimized for RunPod.

## What to expect

The template provisions the official ComfyUI MiniMax H3 model repacks, VAEs and workflows. Basic familiarity with RunPod pods, logs, secrets and file management is useful; normal use does not require Linux administration experience.

## When to use this template

Use this template for MiniMax H3 text-to-video, image-to-video, first/last-frame video and reference-to-video workflows with generated audio.

## 🔧 Features

- Automatic model provisioning through environment variables.
- Full INT8 ConvRot diffusion models for high-VRAM GPUs.
- Pruned INT8 ConvRot diffusion models for lower-VRAM GPUs.
- INT8 ConvRot Qwen3-VL text encoder.
- Official I2V, T2V and R2V workflows.
- CUDA 12.8 runtime with compiled attention acceleration.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.
- LoRA Manager and common video, workflow and utility nodes.

## 📦 Deployment on RunPod

- [RunPod deployment](ComfyUI_MiniMax_deployment.md)

## Example standard workflow Reference to video/audio

![MiniMax H3 workflow Ref2va](images/ai-generated-MiniMax.jpg)

## Example standard workflow image to video/audio

![MiniMax H3 workflow Ref2va](images/ai-generated-MiniMax-i2v.jpg)

## 📘 Tutorial

- [MiniMax tutorial](ComfyUI_MiniMax_tutorial.md)

### Pod running on L40S

![Pod running on L40S](images/runpod_L40S_MiniMax.jpg)

### Pod running on RTX 5090

![Pod running on RTX 5090](images/runpod_A5000_MiniMax.jpeg)

## More information

- [Environment configuration](ComfyUI_MiniMax_configuration.md)
- [Hardware guidance](ComfyUI_MiniMax_hardware.md)
- [Image setup](ComfyUI_MiniMax_image_setup.md)
- [Custom nodes](ComfyUI_MiniMax_custom_nodes.md)
- [Resources](ComfyUI_MiniMax_resources.md)
- [Updates](ComfyUI_MiniMax_update.md)
