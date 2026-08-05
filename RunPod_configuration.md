# ⚙️ Environment Variables

## ComfyUI move to workspace configuration

| Variable                  | Description                                                                    | Default |
|---------------------------|--------------------------------------------------------------------------------|---------|
| `MOVE_STATUS_INTERVAL`    | Seconds between progress updates while moving ComfyUI to the pod volume     | 5       |
| `MOVE_STALL_TIMEOUT`      | Stop the move after this many seconds without a change in copied directory size | 300     |

## ComfyUI Configuration

| Variable                  | Description                                                                    | Default |
|---------------------------|--------------------------------------------------------------------------------|---------|
| `COMFYUI_EXTRA_ARGUMENTS` | Additional arguments for the ComfyUI CLI                                       |         |
| `VRAM_THRESHOLD`          | VRAM threshold in GB for selecting the model                                   | Image: 38 GB; LTX/WAN: 36 GB |
| `COMFYUI_START_MAX_TRIES` | Number of tries to wait until ComfyUI is online; depends on vCPU speed          | 60      |
| `HAS_GPU_BLACKWELL`       | Automatically exported as `1` when a Blackwell GPU is detected; otherwise `0`  | `0`     |

## Authentication Tokens

| Token Source   | Variable         |
|----------------|------------------|
| Code Server    | `PASSWORD`       |
| Hugging Face   | `HF_TOKEN`       |
| CivitAI        | `CIVITAI_TOKEN`  |

## Hugging Face hub model transfer Configuration

| Variable              | Description                                                                                               | Default |
|-----------------------|-----------------------------------------------------------------------------------------------------------|---------|
| `HF_DOWNLOAD_STALL_TIMEOUT` | Stall watchdog for `hf download` in seconds. | `300`   |
| `HF_DOWNLOAD_KILL_AFTER` | Kill grace period `hf download` in seconds. | `30`   |

## Hugging Face ComfyUI Model Configuration

- Change `HF_MODEL_` to `HF_MODEL_LVRAM_` or `HF_MODEL_HVRAM_` to make model loading VRAM dependent through `VRAM_THRESHOLD`.
- Insert `BLACKWELL_` after the standard or VRAM prefix to select models specifically for Blackwell GPUs.

| Selection             | Variable prefix                 |
|-----------------------|---------------------------------|
| Standard              | `HF_MODEL_`                     |
| High VRAM             | `HF_MODEL_HVRAM_`               |
| Low VRAM              | `HF_MODEL_LVRAM_`               |
| Blackwell             | `HF_MODEL_BLACKWELL_`           |
| Blackwell + high VRAM | `HF_MODEL_HVRAM_BLACKWELL_`     |
| Blackwell + low VRAM  | `HF_MODEL_LVRAM_BLACKWELL_`     |

The Blackwell prefixes can be used for every model type in the table below. For example:

```text
HF_MODEL_BLACKWELL_DIFFUSION_MODELS1=org/repository
HF_MODEL_BLACKWELL_DIFFUSION_MODELS_FILENAME1=model.safetensors

HF_MODEL_HVRAM_BLACKWELL_TEXT_ENCODERS1=org/repository
HF_MODEL_HVRAM_BLACKWELL_TEXT_ENCODERS_FILENAME1=text_encoder.safetensors

HF_MODEL_LVRAM_BLACKWELL_VAE1=org/repository
HF_MODEL_LVRAM_BLACKWELL_VAE_FILENAME1=vae.safetensors
```

Blackwell selection and fallback are evaluated separately for each model type and for the VRAM-dependent and VRAM-independent prefixes. A Blackwell variant is selected when at least one matching model and filename pair is configured. When no complete Blackwell pair exists for a model type, the corresponding standard `HF_MODEL_`, `HF_MODEL_HVRAM_`, or `HF_MODEL_LVRAM_` variables are used automatically.

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
| Latent Upscale  | `HF_MODEL_LATENT_UPSCALE[1-20]`      | `HF_MODEL_LATENT_UPSCALE_FILENAME[1-20]`      |
| LoRAs           | `HF_MODEL_LORA[1-20]`                | `HF_MODEL_LORA_FILENAME[1-20]`                |
| VAE TAESD       | `HF_MODEL_VAE_APPROX[1-20]`          | `HF_MODEL_VAE_APPROX_FILENAME[1-20]`          |
| ControlNet      | `HF_MODEL_CONTROLNET[1-20]`          | `HF_MODEL_CONTROLNET_FILENAME[1-20]`          |

## Hugging Face Model Configuration

| Type | Model                   | Safetensors/GGUF          | Include pattern                  | Exclude pattern                  | `/workspace/ComfyUI/<Directory>` |
|------|-------------------------|---------------------------|----------------------------------|----------------------------------|----------------------------------|
| File | `HF_MODEL[1-20]`        | `HF_MODEL_FILENAME[1-20]` | `HF_MODEL_INCLUDE[1-20]`         | `HF_MODEL_EXCLUDE[1-20]`         | `HF_MODEL_DIR[1-20]`             |
| Dir  | `HF_FULL_MODEL[1-20]`   |                           | `HF_FULL_MODEL_INCLUDE[1-20]`    | `HF_FULL_MODEL_EXCLUDE[1-20]`    | `HF_FULL_MODEL_DIR[1-20]`        |

## CivitAI LORAs download Configuration
 
| Variable                         | Description                      |
|----------------------------------|----------------------------------|
| `CIVITAI_COM_MODEL_LORA_ID[1-50]`   | Version ID for LoRA (AIR) |
| `CIVITAI_COM_MODEL_UNET_ID[1-50]`   | Version ID for UNET (AIR) |
| `CIVITAI_RED_MODEL_LORA_ID[1-50]`   | Version ID for LoRA (AIR) |
| `CIVITAI_RED_MODEL_UNET_ID[1-50]`   | Version ID for UNET (AIR) |

## Workflows download Configuration

- Change `WORKFLOW` to `WORKFLOW_LVRAM` or `WORKFLOW_HVRAM` makes loading VRAM dependent. Makes loading VRAM dependent through `VRAM_THRESHOLD`.

| Variable         | Description                      |
|------------------|----------------------------------|
| `WORKFLOW[1-50]` | Download link (compressed or plain) |

## Media download Configuration

| Variable         | Description                      |
|------------------|----------------------------------|
| `MEDIA[1-50]` | Download link |

## 🌐 Available Network Services

| Service       | Port   | Access Type |
|---------------|--------|-------------|
| ComfyUI       | `8188` | Web         |
| Code Server   | `9000` | Web         |
| SSH/SCP       | `22`   | Terminal    |
