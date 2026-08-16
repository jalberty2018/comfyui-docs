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
- 4-step , 8-step Turbo-loras (turbo and lightx2v) included

## 📦 Deployment on RunPod

- [RunPod deployment](ComfyUI_MiniMax_deployment.md)

## 📘 Tutorial

- [MiniMax tutorial](ComfyUI_tutorial.md)

## Example standard workflow Reference to video/audio (Ref2va) with or without turbo

![MiniMax H3 workflow Ref2va](images/ai-generated-MiniMax.jpg)

## Example standard workflow image to video/audio (fl2va) with or without turbo

![MiniMax H3 workflow i2v](images/ai-generated-MiniMax-i2v.jpg) with or without turbo

## Example standard workflow text to video/audio (fl2va) with or without turbo

![MiniMax H3 workflow t2v](images/ai-generated-MiniMax-t2v.jpg)

## Example workflow all in one with or without turbo

![MiniMax H3 workflow all in one](images/ai-generated-MiniMax-director.jpg)

## Example experimental workflow with 3 x 15 seconds multi-shot from one reference image (Ref2va)

![MiniMax H3 workflow multi-shot](images/ai-generated-MiniMax-multi-shot.jpg)

## Example video with Ref2va

<div style="text-align: center;">
  <video controls preload="metadata" style="max-width: 50%; height: auto;">
    <source src="/video/Video_tickling_princess.mp4" type="video/mp4">
  </video>
</div>

## Example video with fl2va

### i2v

<div style="text-align: center;">
  <video controls preload="metadata" style="max-width: 50%; height: auto;">
    <source src="/video/Video_girl_drinking_cocktail.mp4" type="video/mp4">
  </video>
</div>

### t2v

<div style="text-align: center;">
  <video controls preload="metadata" style="max-width: 50%; height: auto;">
    <source src="/video/Video_girl_walking_on_beach.mp4" type="video/mp4">
  </video>
</div>

## Example video with director

<div style="text-align: center;">
  <video controls preload="metadata" style="max-width: 50%; height: auto;">
    <source src="/video/Video_minimax_slow.mp4" type="video/mp4">
  </video>
</div>

## Example video multi-shot (45 seconds video generated on RTX 5090)

<div style="text-align: center;">
  <video controls preload="metadata" style="max-width: 50%; height: auto;">
    <source src="/video/Video_minimax_multi-shot.mp4" type="video/mp4">
  </video>
</div>

### Pod running on L40S (good quality)

![Pod running on L40S](images/runpod_L40S_MiniMax.jpg)

### Pod running on RTX 5090 (fast but restricted in resolution and duration)

![Pod running on RTX 5090](images/runpod_A5000_MiniMax.jpeg)

### Pod running on RTX PRO 6000 (fast and no restrictions)

![Pod running on RTX PRO 6000](images/runpod_RTXPRO6000_MiniMax.jpg)

### Pod running on RTX 3090/4090 (slow and restricted in resolution and duration)

![Pod running on RTX 3090](images/runpod_RTX3090_MiniMax.jpg)

## More information

- [Environment configuration](RunPod_configuration.md)
- [Hardware guidance](ComfyUI_MiniMax_hardware.md)
- [Image setup](ComfyUI_MiniMax_image_setup.md)
- [Custom nodes](ComfyUI_MiniMax_custom_nodes.md)
- [Resources](ComfyUI_MiniMax_resources.md)
- [Updates](ComfyUI_MiniMax_update.md)
