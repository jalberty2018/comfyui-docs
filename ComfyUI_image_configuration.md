# ⚙️ Environment variables

## Configuration

| Variable                   | Description                    | default |
|-------------------|-------------------------------|-------------------------------------------|
| `COMFYUI_EXTRA_ARGUMENTS`  | Additional arguments for ComfyUI CLI |   |
| `VRAM_THRESHOLD`  | VRAM threshold in GB for selecting model/worflow | 38 Gb |



## Authentication Tokens

| Token Source   | Variable         | 
|----------------|------------------|
| Code Server    | `PASSWORD`       | 
| Hugging Face   | `HF_TOKEN`       | 
| CivitAI        | `CIVITAI_TOKEN`  | 

## Huggingface ComfyUI Model Configuration

- Changing HF_MODEL_ to HF_MODEL_LVRAM_ and HF_MODEL_HVRAM_ makes the loading VRAM dependent (VRAM_THRESHOLD) 

| Model Type        | Model                         | Safetensors/GGUF                               |
|-------------------|-------------------------------|-------------------------------------------| 
| Diffusion Model   | `HF_MODEL_DIFFUSION_MODELS[1-20]`          | `HF_MODEL_DIFFUSION_MODELS_FILENAME[1-20]`   |
| Checkpoints       | `HF_MODEL_CHECKPOINTS[1-20]`        | `HF_MODEL_CHECKPOINTS_FILENAME[1-20]`        |
| Text Encoders     | `HF_MODEL_TEXT_ENCODERS[1-20]` | `HF_MODEL_TEXT_ENCODERS_FILENAME[1-20]` |
| Clip Vision       | `HF_MODEL_CLIP_VISION[1-20]`        | `HF_MODEL_CLIP_VISION_FILENAME[1-20]` |
| Audio Encoders    | `HF_MODEL_AUDIO_ENCODERS[1-20]` | `HF_MODEL_AUDIO_ENCODERS_FILENAME[1-20]` |
| Model patches    | `HF_MODEL_PATCHES[1-20]` | `HF_MODEL_PATCHES_FILENAME[1-20]` |
| VAE               | `HF_MODEL_VAE[1-20]`                | `HF_MODEL_VAE_FILENAME[1-20]`                |
| Upscalers         | `HF_MODEL_UPSCALER[1-20]`      | `HF_MODEL_UPSCALER_PTH[1-20]`              |
| Loras          | `HF_MODEL_LORA[1-20]`          | `HF_MODEL_LORA_FILENAME[1-20]`          |
| VAE taesd          | `HF_MODEL_VAE_APPROX[1-20]`          | `HF_MODEL_VAE_APPROX_FILENAME[1-20]`          |

## Huggingface model configuration

| Type  | Model     | Safetensors/GGUF |  /workspace/ComfyUI/<Directory> |
|-------|-----------|------------------|---------------------------------|  
| File  | `HF_MODEL[1-20]`  | `HF_MODEL_FILENAME[1-20]`   | `HF_MODEL_DIR[1-20]` |
| Dir   | `HF_FULL_MODEL[1-20]`  |   | `HF_FULL_MODEL_DIR[1-20]` |

## CivitAI LORAs

| Variable                         | Description                      |
|----------------------------------|----------------------------------|
| `CIVITAI_MODEL_LORA_URL[1-50]`   | Direct download link for LoRAs |
| `CIVITAI_MODEL_UNET_URL[1-50]`   | Direct download link for URL's |

## Workflows/Media

- Changing WORKFLOW to WORKFLOW_LVRAM and WORKFLOW_HVRAM makes the loading VRAM dependent (cut off 40Gb) 

| Variable         | Description                      |
|------------------|----------------------------------|
| `WORKFLOW[1-50]` |  download link (compressed or plain) |
| `MEDIA[1-50]` |  download link |

## 🌐 Network Services

| Service       | Port   | Access Type |
|---------------|--------|-------------|
| ComfyUI       | `8188` | Web         |
| Code Server   | `9000` | Web         |
| SSH/SCP       | `22`   | Terminal    |
