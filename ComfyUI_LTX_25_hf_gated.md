# LTX-2.5 model license

## Accepting the license

- Log in to or create a Hugging Face account (free).
- Open the gated [Lightricks/LTX-2.5 model repository](https://huggingface.co/Lightricks/LTX-2.5).
- Read the [LTX-2 Community License Agreement](https://github.com/Lightricks/LTX-2/blob/main/LICENSE.md) and the information on the access form.
- Click **Agree and Access**. Access is normally granted automatically.
- Create or use a Hugging Face token. A read token is sufficient; a
  fine-grained token must have read access to `Lightricks/LTX-2.5` or to public
  gated repositories you can access.
- Choose between the following options.

Access belongs to the individual Hugging Face account that accepted the terms.
A token from another account will not inherit that access.

## Option 1: Before starting the template

- Click **Edit Template** and expand the Environment Variables section.
- Add your token or RunPod secret to **HF_TOKEN**.
- For a private template, the supplied environment profiles use:

```text
HF_TOKEN={{ RUNPOD_SECRET_HF_TOKEN_WRITE }}
```

- Create the `HF_TOKEN_WRITE` RunPod secret first, or change the reference to
  your existing secret name.
- **Save the template**.
- Click **Deploy On-Demand**.
- The template will download the selected LTX-2.5 transformer, text encoder,
  distilled LoRA, VAEs, upscalers, and model patch.

Never save a real Hugging Face token in a public template.

## Option 2: When the pod is running

### Set your Hugging Face token

- Open a terminal from the console or Code Server (see [tutorial](ComfyUI_tutorial.md)).
- Fill in your Hugging Face token (`HF_TOKEN`).

```bash
export HF_TOKEN=Your-hf-token-here
```

or

```bash
hf auth login
```

- Press enter.
- Verify the connected account and gated repository access.

```bash
hf auth whoami
hf download Lightricks/LTX-2.5 \
  diffusion_models/ltx-2.5-22b-dev-transformer-comfy-int8-convrot.safetensors \
  --dry-run
```

- Manual provision from the documentation available in the pod
- Press enter.
- Wait until the download finishes.
- Restart the pod if the startup provisioning previously failed; existing
  files will be skipped and the remaining chain will be downloaded.
