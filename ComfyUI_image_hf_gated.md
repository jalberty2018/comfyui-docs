# Flux.2 Klein 9B model download

## Accepting licenses

- Difference between models and license [flux-2-klein-4b-vs-9b-comparison](https://apatero.com/blog/flux-2-klein-4b-vs-9b-comparison)

- Login of create a account on huggingface (free).
- Accept the [license distilled](https://huggingface.co/black-forest-labs/FLUX.2-klein-9B) on huggingface
- Accept the [license base](https://huggingface.co/black-forest-labs/FLUX.2-klein-base-9B) on huggingface
- Create or use a huggingface token (free).
- Choose between the following options.

## Option 1: Before starting the template

- Click **Edit Template** and expand the Environment Variables section.
- Add your token/secret to **HF_TOKEN**.
- **Save the template**.
- Click **Deploy On-Demand**
- The template will download the 4B and 9B models.

## Option 2: When the pod is running

- Open terminal from the console or code-server (see [tutorial](ComfyUI_image_tutorial))

```bash
export HF_TOKEN=Your-hf-token-here
hf download black-forest-labs/FLUX.2-klein-9B flux-2-klein-9b.safetensors \
--local-dir /workspace/ComfyUI/models/diffusion_models/
hf download black-forest-labs/FLUX.2-klein-base-9B flux-2-klein-base-9b.safetensors \
--local-dir /workspace/ComfyUI/models/diffusion_models/
```

- Fill in your huggingface token (HF_TOKEN)
- Copy and paste snippet in terminal.
- press enter.
- Wait until downloads ends.
- In ComfyUI press r to refresh.

## Speeding up model downloads

- If you don't need the 4B model delete the following keys in the template before starting the pod.

```txt
HF_MODEL_DIFFUSION_MODELS3
HF_MODEL_DIFFUSION_MODELS_FILENAME3
HF_MODEL_DIFFUSION_MODELS4
HF_MODEL_DIFFUSION_MODELS_FILENAME4
HF_MODEL_TEXT_ENCODERS2
HF_MODEL_TEXT_ENCODERS_FILENAME2
```
