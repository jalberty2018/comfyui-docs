# ⚙️ Environment Variables

## ComfyUI move to workspace configuration

| Variable                  | Description                                                                    | Default |
|---------------------------|--------------------------------------------------------------------------------|---------|
| `MOVE_STATUS_INTERVAL`    | Seconds between progress updates while moving ComfyUI to the pod volume     | 5       |
| `MOVE_STALL_TIMEOUT`      | Stop the move after this many seconds without a change in copied directory size | 300     |

## ComfyUI Configuration

- VRAM_TRESHHOLD_BLACKWELL is only available for MiniMax and Image2 pod.

| Variable                  | Description                                                                    | Default |
|---------------------------|--------------------------------------------------------------------------------|---------|
| `COMFYUI_EXTRA_ARGUMENTS` | Additional arguments for the ComfyUI CLI                                       |         |
| `VRAM_THRESHOLD`          | VRAM threshold in GB for selecting the model                                   | Image: 38 GB; LTX/WAN: 36 GB |
| `VRAM_TRESHHOLD_BLACKWELL` | VRAM threshold in GB for selecting Blackwell-specific high- or low-VRAM models | MiniMax: 40 GB |
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

Choose the prefix that matches when the model should be downloaded:

| Condition | Prefix |
|-----------|--------|
| Every GPU, independent of VRAM | `HF_MODEL_` |
| Every Blackwell GPU, independent of VRAM | `HF_MODEL_BLACKWELL_` |
| More VRAM than `VRAM_THRESHOLD` | `HF_MODEL_HVRAM_` |
| VRAM equal to or below `VRAM_THRESHOLD` | `HF_MODEL_LVRAM_` |
| Blackwell with more VRAM than `VRAM_TRESHHOLD_BLACKWELL` | `HF_MODEL_HVRAM_BLACKWELL_` |
| Blackwell with VRAM equal to or below `VRAM_TRESHHOLD_BLACKWELL` | `HF_MODEL_LVRAM_BLACKWELL_` |

`VRAM_TRESHHOLD_BLACKWELL` defaults to 40 GB in the MiniMax image. For example, a 48 GB Blackwell GPU selects the high-VRAM pair below, while a 32 GB or 40 GB Blackwell GPU selects the low-VRAM pair:

```text
HF_MODEL_HVRAM_BLACKWELL_DIFFUSION_MODELS1=org/high-vram-model
HF_MODEL_HVRAM_BLACKWELL_DIFFUSION_MODELS_FILENAME1=high-vram-model.safetensors

HF_MODEL_LVRAM_BLACKWELL_DIFFUSION_MODELS1=org/low-vram-model
HF_MODEL_LVRAM_BLACKWELL_DIFFUSION_MODELS_FILENAME1=low-vram-model.safetensors
```

Always configure both the model and filename variable. Selection is evaluated per model type. If no complete matching Blackwell pair exists, the corresponding standard high- or low-VRAM pair is used automatically.

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
