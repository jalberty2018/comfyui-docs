# run-comfyui-minimax

## Release Notes Policy

- A new dated section is added whenever a new stable ComfyUI release is included.
- The date is updated whenever custom nodes, provisioning, or runtime behavior change.
- This pod is stable, but many of its custom nodes are changing with every version.
- Some custom nodes have been adapted specifically for this pod or pinned to increase the stability.
- Tested on L40S, RTX PRO 6000, PRO 6000 MiG 48Gb, RTX 5090, (RTX 4090).

## 24092026

- ComfyUI 0.37.1
- Pytorch 2.12.1 CUDA 13.0 build
- llama-cpp b11115
- [comfyui-obvpm-timeline](https://github.com/chanon/comfyui-obvpm-timeline)

## Container CUDA upgrade notice

- run-comfyui-minimax requires CUDA 13.x (due to breaking changes in "comfy-kitchen" and no support for CUDA 12.x on modern GPU's by ComfyUI).
- If you need due GPU shortage a instance change runpod container template tag to run-comfyui-minimax:21092026.

## 21092026

- ComfyUI 0.37.0
- Last tested version running on CUDA 12.8

## 20092026

- ComfyUI 0.36.0
- Removed unused custom nodes.
- Lowered pod size by excluding unused media in custom_nodes
- Added GPU-accelerated video encoding with FFmpeg and NVENC to speed up video creation on slower vCPUs.
- Auto detect NVENC availability on host.
- Updated worklows to use nvenc video encoding.
- Forked and customized model_linker.
- Added another video VAE to reduce memory usage (does not work with pruned models).
- Updated Lora-Manager template.
- Forked and fixed VHS : video upload without audio regression.
- [ComfyUI-Hyperflow](https://github.com/Saganaki22/ComfyUI-Hyperflow)
- Added workflows Hyperflow 8 step.
- [comfyui-obvpm](https://github.com/chanon/comfyui-obvpm)

## 15092026

- ComfyUI 0.35.0
- Updated workflows.
- Tail is an optional download.
- Switched Blackwell HVRAM diffusion models to standard INT8 ConvRot for better compatibility.

## 08092026

- ComfyUI 0.34.0
- [ComfyUI-MiniMax-H3-PDD-Acc](https://github.com/Jalen-Brunson/ComfyUI-MiniMax-H3-PDD-Acc)
- [MMH3-UltimateUpscale](https://github.com/bbaudio-2025/Comfyui-MMH3-UltimateUpscale)
- Fixed Multi-shot audio crash.
- Removed custom_nodes using irriversible patching
- Security updates

## 25082026

- ComfyUI 0.33.0
- Fixed THRESHOLD typo.
- Updated configuration for RTX PRO 6000 for higher quality.
- Changed configuration diffusion model LVRAM BACKWELL for lora compatibility.
- Added local llama-cpp (cli,server) support
- Added separate RunPod templates for local Qwen-VL prompt enhancement with llama.cpp; see the deployment guide for more information.
- Added uncensored profile to_QWEN_H3_prompt modified workflows.
- Fixed crash mult-shot context pin after first shot in workflows (sol attention)
- [ComfyUI-H3-Qwen3VL-TextGen](https://github.com/ethanfel/ComfyUI-H3-Qwen3VL-TextGen)
- [MiniMax H3 Audio T8](https://github.com/T8mars/comfyui-minimax-h3-audio-T8)
- [ComfyUI_Qwen_H3_Prompt](https://github.com/chflame163/ComfyUI_Qwen_H3_Prompt)

## 13082026

- ComfyUI 0.32.0
- [ComfyUI-H3-Motion-Context](https://github.com/NikoDemon80/ComfyUI-H3-Motion-Context)

## 11082026

- ComfyUI 0.31.0
- sm_120 (Blackwell) attentions added.
- llama-cpp-python added for sm_120.
- Updated base image.
- [ComfyUI-sol-attn](https://github.com/Saganaki22/ComfyUI-sol-attn)
- [ComfyUI-H3-multishot](https://github.com/jlucasmcrell/ComfyUI-H3-Multishot)
- [ComfyUI-H3-PowerLoraStack](https://github.com/cicalooo/ComfyUI-H3-PowerLoraStack)
- [ComfyUI-MiniMaxH3-Preview](https://github.com/Brioch/ComfyUI-MiniMaxH3-Preview)

## 07082026

- ComfyUI 0.30.0
- [ComfyUI-SolAttn_triton](https://github.com/kijai/ComfyUI-SolAttn_triton)
- [ComfyUI-Fantastic-MiniMaxH3-PromptBuilder](https://github.com/Adudeguyman/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder)
- [ComfyUI_MiniMaxH3_Director](https://github.com/AIMixer/ComfyUI_MiniMaxH3_Director)
- [ComfyUI-Spectrum](https://github.com/xmarre/ComfyUI-Spectrum-MiniMax-H3)
- [ComfyUI-MiniMax-H3-Turbo](https://github.com/Larryvrh/ComfyUI-MiniMax-H3-Turbo)
- [ComfyUI-MiniMaxH3-FirstBlockCache](https://github.com/duckyshell/ComfyUI-MiniMaxH3-FirstBlockCache)
- Configurations for models download depending on GPU architecture and VRAM.
- Added experimental turbo loras from different developers.
