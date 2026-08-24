# 🚀 Template Deployment RunPod

- The MiniMax image is intended for NVIDIA CUDA GPUs.

## 🚀 Template

| Template | Tasks | Inputs | Output |
|---|---|---|---|
| MiniMax H3 FL2VA | Text-to-video, image-to-video and first/last-frame-to-video | Text with optional first and/or last frame | Video with audio |
| MiniMax H3 Ref2VA | Reference-to-video | Text with reference images, video and/or audio | Video with audio |

### **Two prompt-enhancement options are available**

- The **tail** uses the MiniMax H3 text encoder and is slower.
- The **QWEN prompt enhancer** uses a second, separate Qwen model together with llama.cpp for faster prompt generation.
- Both are only needed for prompt enhancement, not for inference with the MiniMax H3 model itself.

### Links to the templates

- [**👉 One-click Deploy MiniMax H3 FL2VA plus tail**](https://console.runpod.io/deploy?template=v7b5g03csk&ref=se4tkc5o)
- [**👉 One-click Deploy MiniMax H3 Ref2VA plus tail**](https://console.runpod.io/deploy?template=6qtfx7lxgc&ref=se4tkc5o)
- [**👉 One-click Deploy MiniMax H3 FL2VA plus prompt enhancer**](https://console.runpod.io/hub/template/a1nkufhzxq?ref=se4tkc5o)
- [**👉 One-click Deploy MiniMax H3 Ref2VA plus prompt enhancer**](https://console.runpod.io/hub/template/pcsqepl6kt?ref=se4tkc5o)

## 🏷️ Container date tags

The dated image tag used by a RunPod template can remain on an earlier validated build when a newer image has not yet been tested for this model.

## 📘 Tutorial

- [Specific for this template](ComfyUI_tutorial.md)

## 💻 Hardware requirements

- [GPU selection](ComfyUI_MiniMax_hardware.md)

## ⚙️ Configuration

- [RunPod configuration](RunPod_configuration.md)
