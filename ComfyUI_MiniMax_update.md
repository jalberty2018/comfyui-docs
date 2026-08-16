# run-comfyui-minimax

## Release Notes Policy

- A new dated subtitle is added whenever a new stable ComfyUI release is included.
- The date is updated when custom nodes, provisioning or runtime behavior changes.
- Pinned custom nodes are not updated automatically because pin changes can introduce compatibility issues.
- This pod is stable but many custom_nodes and turbo loras are experimental and in full development.
- Tested on L40S, RTX 4090, RTX 3090, RTX 5090 and RTX PRO 6000.

## 16082026

- ComfyUI 0.33.0
- Fixed THRESHOLD typo.
- Updated configuration for RTX PRO 6000 for higher quality.
- Changed configuration diffusion model LVRAM BACKWELL for lora compatibility.
- [ComfyUI-H3-Qwen3VL-TextGen](https://github.com/ethanfel/ComfyUI-H3-Qwen3VL-TextGen.git)


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
- [ComfyUI-MiniMax-H3-Guide](https://github.com/ethanfel/ComfyUI-MiniMax-H3-Guide)
- [ComfyUI-SolAttn_triton](https://github.com/kijai/ComfyUI-SolAttn_triton)
- [ComfyUI-Fantastic-MiniMaxH3-PromptBuilder](https://github.com/Adudeguyman/ComfyUI-Fantastic-MiniMaxH3-PromptBuilder)
- [ComfyUI_MiniMaxH3_Director](https://github.com/AIMixer/ComfyUI_MiniMaxH3_Director)
- [ComfyUI-Spectrum](https://github.com/xmarre/ComfyUI-Spectrum-MiniMax-H3)
- [ComfyUI-MiniMax-H3-Turbo](https://github.com/Larryvrh/ComfyUI-MiniMax-H3-Turbo)
- [ComfyUI-MiniMaxH3-FirstBlockCache](https://github.com/duckyshell/ComfyUI-MiniMaxH3-FirstBlockCache)
- Configurations for models download depending on GPU architecture and VRAM.
- Added experimental turbo loras from different developers.
