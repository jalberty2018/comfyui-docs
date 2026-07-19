# FLUX.2 Klein 9B model license

## Accepting licenses

- Difference between models and licenses: [FLUX.2 Klein 4B vs 9B comparison](https://apatero.com/blog/flux-2-klein-4b-vs-9b-comparison)

- Log in or create a Hugging Face account (free).
- Accept the [distilled model license](https://huggingface.co/black-forest-labs/FLUX.2-klein-9B) on Hugging Face.
- Accept the [base model license](https://huggingface.co/black-forest-labs/FLUX.2-klein-base-9B) on Hugging Face.
- Create or use a Hugging Face token (free).
- Choose between the following options.

## Option 1: Before starting the template

- Click **Edit Template** and expand the Environment Variables section.
- Add your token/secret to **HF_TOKEN**.
- **Save the template**.
- Click **Deploy On-Demand**.
- The template will download the 9B model.

## Option 2: When the pod is running

### Set your Hugging Face token

- Open terminal from the console or code-server (see [tutorial](ComfyUI_image_tutorial.md))
- Fill in your Hugging Face token (`HF_TOKEN`).

```bash
export HF_TOKEN=Your-hf-token-here
```

or

```bash
hf auth login
```

- Press enter.
- Copy and paste one or both model downloads in the terminal.

### Distilled model

```bash
hf download black-forest-labs/FLUX.2-klein-9B flux-2-klein-9b.safetensors \
--local-dir /workspace/ComfyUI/models/diffusion_models/
```

- Press enter.

### Base model

```bash
hf download black-forest-labs/FLUX.2-klein-base-9B flux-2-klein-base-9b.safetensors \
--local-dir /workspace/ComfyUI/models/diffusion_models/
```

- Press enter.
- Wait until the downloads finish.