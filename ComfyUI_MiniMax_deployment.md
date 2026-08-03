# 🚀 Template Deployment RunPod

- The MiniMax image is intended for NVIDIA CUDA GPUs.

## 🚀 Template


| Checkpoint | Supported Tasks | Input Conditions | Output | 
|---|---|---|---|
| MiniMax-H3 Base FL2VA | Text-to-Audio-Video (`t2va`), First/Last-Frame-to-Audio-Video (`fl2va`) | Text; optional first frame, last frame, or both | Video and audio |
| MiniMax-H3 Base Ref2VA | Reference-to-Audio-Video (`ref2va`) | Text with reference images, videos, and/or audio | Video and audio |

- [**👉 One-click Deploy on RunPod MiniMax H3 FL2VA  **](https://console.runpod.io/deploy?template=v7b5g03csk&ref=se4tkc5o)
- [**👉 One-click Deploy on RunPod MiniMax H3 Ref2VA **](https://console.runpod.io/deploy?template=6qtfx7lxgc&ref=se4tkc5o)

## 🏷️ Container date tags

The dated image tag used by a RunPod template can remain on an earlier validated build when a newer image has not yet been tested for this model.

## 📘 Tutorial

- [Specific for this template](ComfyUI_MiniMax_tutorial.md)

## 💻 Hardware requirements

- [GPU selection](ComfyUI_MiniMax_hardware.md)

## ⚙️ Configuration

- [RunPod configuration](RunPod_configuration.md)
