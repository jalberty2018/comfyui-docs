# 🚀 Template Deployment RunPod

- Tested using **L40S**, **RTX 6000 Ada**, **RTX A5000** and **RTX 4090** GPUs.
- ⚠️ Don't use pods with **no region id**; they are unreliable.

### 🚀 Template

- [**👉 One-click Deploy on RunPod LTX-2.5 i2v/t2v vi2v/vt2v dev bf16/int8 convrot**](https://console.runpod.io/deploy?template=ka3hvli4kf&ref=se4tkc5o)
- [**👉 One-click Deploy on RunPod LTX-2.3 i2v/t2v vi2v/vt2v dev bf16/fp8**](https://console.runpod.io/deploy?template=p4f6rm9tb4&ref=se4tkc5o)

### 🏷️ Container date tags

- The container date tag used by a RunPod template, for example `01072026`, can differ between models. This is intentional: a template may stay on an earlier validated container when a newer build has not yet been tested with that specific model, or when only minor changes were made compared with the previous version.

## 📘 Tutorial

- [Specific for this template](ComfyUI_tutorial.md)
- [Accept the gated LTX-2.5 license](ComfyUI_LTX_25_hf_gated.md)

### 💻 Hardware requirements

- [GPU selection](ComfyUI_LTX_hardware.md)

### ⚙️ Configuration

- [RunPod configuration](RunPod_configuration.md)
