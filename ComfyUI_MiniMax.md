[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-minimax)](https://hub.docker.com/r/ls250824/run-comfyui-minimax)

# MiniMax inference with ComfyUI

A streamlined and automated environment for running **ComfyUI** with **MiniMax H3 video and native-audio generation**, optimized for RunPod.

## What to expect

The template provisions the official ComfyUI MiniMax H3 model repacks, VAEs and workflows. Basic familiarity with RunPod pods, logs, secrets and file management is useful; normal use does not require Linux administration experience.

## When to use this template

Use this template for MiniMax H3 text-to-video, image-to-video, first/last-frame video and reference-to-video workflows with generated audio.

## 🔧 Features

- Automatic model provisioning through environment variables.
- Models downloads depending on VRAM and architecture (Ada Lovelace / Blackwell).
- CUDA 12.8 runtime with compiled attention acceleration.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.
- Uncensored heretic QWEN VL text encoder.
- LoRA Manager
- Installed custom nodes and accelerators.
- Example workflows.
- Turbo-lora (experimental)

## 📦 Deployment on RunPod

- [RunPod deployment](ComfyUI_MiniMax_deployment.md)

## 📘 Tutorial

- [MiniMax tutorial](ComfyUI_MiniMax_tutorial.md)

## Example standard workflow Reference to video/audio (Ref2va)

![MiniMax H3 workflow Ref2va](images/ai-generated-MiniMax.jpg)

## Example standard workflow image to video/audio (fl2va)

![MiniMax H3 workflow i2v](images/ai-generated-MiniMax-i2v.jpg)

## Example standard workflow with director custom node

![MiniMax H3 workflow director](images/ai-generated-MiniMax-director.jpg)

### Pod running on L40S

![Pod running on L40S](images/runpod_L40S_MiniMax.jpg)

### Pod running on RTX 5090

![Pod running on RTX 5090](images/runpod_A5000_MiniMax.jpeg)

### Pod running on RTX PRO 6000

![Pod running on RTX PRO 6000](images/runpod_RTXPRO6000_MiniMax.jpg)

## More information

- [Environment configuration](ComfyUI_MiniMax_configuration.md)
- [Hardware guidance](ComfyUI_MiniMax_hardware.md)
- [Image setup](ComfyUI_MiniMax_image_setup.md)
- [Custom nodes](ComfyUI_MiniMax_custom_nodes.md)
- [Resources](ComfyUI_MiniMax_resources.md)
- [Updates](ComfyUI_MiniMax_update.md)
