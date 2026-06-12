# ⚙️ Environment Variables

## Configuration

| Variable                  | Description                                                           | Default |
|---------------------------|-----------------------------------------------------------------------|---------|
| `COMFYUI_EXTRA_ARGUMENTS` | Additional arguments for the ComfyUI CLI                              |         |
| `VRAM_THRESHOLD`          | VRAM threshold in GB for selecting the model/workflow                 | 38 GB   |
| `COMFYUI_START_MAX_TRIES` | Number of tries to wait until ComfyUI is online; depends on vCPU speed | 60      |

## Authentication Tokens

| Token Source   | Variable         | 
|----------------|------------------|
| Code Server    | `PASSWORD`       | 
| Hugging Face   | `HF_TOKEN`       | 
| CivitAI        | `CIVITAI_TOKEN`  | 

## Hugging Face ComfyUI Model Configuration

- Changing `HF_MODEL_` to `HF_MODEL_LVRAM_` and `HF_MODEL_HVRAM_` makes loading VRAM dependent through `VRAM_THRESHOLD`.

| Model Type      | Model                                | Safetensors/GGUF                              |
|-----------------|--------------------------------------|-----------------------------------------------|
| Diffusion Model | `HF_MODEL_DIFFUSION_MODELS[1-20]`    | `HF_MODEL_DIFFUSION_MODELS_FILENAME[1-20]`    |
| Checkpoints     | `HF_MODEL_CHECKPOINTS[1-20]`         | `HF_MODEL_CHECKPOINTS_FILENAME[1-20]`         |
| Text Encoders   | `HF_MODEL_TEXT_ENCODERS[1-20]`       | `HF_MODEL_TEXT_ENCODERS_FILENAME[1-20]`       |
| CLIP Vision     | `HF_MODEL_CLIP_VISION[1-20]`         | `HF_MODEL_CLIP_VISION_FILENAME[1-20]`         |
| Audio Encoders  | `HF_MODEL_AUDIO_ENCODERS[1-20]`      | `HF_MODEL_AUDIO_ENCODERS_FILENAME[1-20]`      |
| Model Patches   | `HF_MODEL_PATCHES[1-20]`             | `HF_MODEL_PATCHES_FILENAME[1-20]`             |
| VAE             | `HF_MODEL_VAE[1-20]`                 | `HF_MODEL_VAE_FILENAME[1-20]`                 |
| Upscalers       | `HF_MODEL_UPSCALER[1-20]`            | `HF_MODEL_UPSCALER_PTH[1-20]`                 |
| LoRAs           | `HF_MODEL_LORA[1-20]`                | `HF_MODEL_LORA_FILENAME[1-20]`                |
| VAE TAESD       | `HF_MODEL_VAE_APPROX[1-20]`          | `HF_MODEL_VAE_APPROX_FILENAME[1-20]`          |
| ControlNet      | `HF_MODEL_CONTROLNET[1-20]`          | `HF_MODEL_CONTROLNET_FILENAME[1-20]`          |

## Hugging Face Model Configuration

| Type | Model                   | Safetensors/GGUF          | `/workspace/ComfyUI/<Directory>` |
|------|-------------------------|---------------------------|----------------------------------|
| File | `HF_MODEL[1-20]`        | `HF_MODEL_FILENAME[1-20]` | `HF_MODEL_DIR[1-20]`             |
| Dir  | `HF_FULL_MODEL[1-20]`   |                           | `HF_FULL_MODEL_DIR[1-20]`        |

## CivitAI LORAs

| Variable                         | Description                      |
|----------------------------------|----------------------------------|
| `CIVITAI_COM_MODEL_LORA_ID[1-50]`   | Version ID for LoRA (AIR) |
| `CIVITAI_COM_MODEL_UNET_ID[1-50]`   | Version ID for UNET (AIR) |
| `CIVITAI_RED_MODEL_LORA_ID[1-50]`   | Version ID for LoRA (AIR) |
| `CIVITAI_RED_MODEL_UNET_ID[1-50]`   | Version ID for UNET (AIR) |

## Workflows

- Changing `WORKFLOW` to `WORKFLOW_LVRAM` and `WORKFLOW_HVRAM` makes loading VRAM dependent through `VRAM_THRESHOLD`.

| Variable         | Description                      |
|------------------|----------------------------------|
| `WORKFLOW[1-50]` | Download link (compressed or plain) |

## Other

| Variable         | Description                      |
|------------------|----------------------------------|
| `MEDIA[1-50]` | Download link |

## 🌐 Network Services

| Service       | Port   | Access Type |
|---------------|--------|-------------|
| ComfyUI       | `8188` | Web         |
| Code Server   | `9000` | Web         |
| SSH/SCP       | `22`   | Terminal    |
