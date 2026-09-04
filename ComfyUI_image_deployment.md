<a id="template-deployment"></a>

# Deploy image models on RunPod

Use this page to choose an image-generation or image-editing template, deploy it on a suitable NVIDIA GPU and open ComfyUI. The templates contain different model families, so choose one based on the task you want to perform.

## Quick recommendation

- Start with **Z-Image Turbo and Base** for straightforward text-to-image generation on a tested 20 GB VRAM configuration.
- Choose **Krea-2 Base and Turbo** for identity, composition and broader image workflows.
- Choose **Qwen-Image-Edit 2511** when an existing image is your main input.
- Choose **FLUX.2 Klein** for control or reference-image workflows, after checking the 9B license requirements.

1. Choose a [template](#choose-a-template).
2. Check its [hardware and storage requirements](#before-you-deploy).
3. Open the RunPod deployment link and configure the pod.
4. Wait until the container log reports that the pod is ready.
5. Open **Connect → HTTP Services → ComfyUI (port 8188)**.

<a id="runpod-templates"></a>

## Choose a template

| Template | Best suited to | RunPod |
| --- | --- | --- |
| **Krea-2 Base and Turbo** | Text-to-image, identity transfer, composition and image-editing workflows | [**Deploy Krea-2 →**](https://console.runpod.io/deploy?template=e2hlyrm22l&ref=se4tkc5o) |
| **Z-Image Turbo and Base** | General and fast text-to-image generation | [**Deploy Z-Image →**](https://console.runpod.io/deploy?template=ia5t70hfak&ref=se4tkc5o) |
| **ERNIE-Image Base and Turbo** | ERNIE text-to-image workflows | [**Deploy ERNIE-Image →**](https://console.runpod.io/deploy?template=g8ow1s1s0a&ref=se4tkc5o) |
| **FLUX.2 Dev** | High-quality generation and multiple-angle workflows | [**Deploy FLUX.2 Dev →**](https://console.runpod.io/deploy?template=8nl523gts5&ref=se4tkc5o) |
| **FLUX.2 Klein** | Control, target and reference-image workflows | [**Deploy FLUX.2 Klein →**](https://console.runpod.io/deploy?template=n1wa3lb44l&ref=se4tkc5o) |
| **Qwen-Image 2512** | Qwen text-to-image generation | [**Deploy Qwen-Image →**](https://console.runpod.io/deploy?template=3fri17sxaa&ref=se4tkc5o) |
| **Qwen-Image-Edit 2511** | Image editing and multiple viewing angles | [**Deploy Qwen-Image-Edit →**](https://console.runpod.io/deploy?template=mxvvx0hcmp&ref=se4tkc5o) |

Each template includes workflows for its model family. After deployment, use the workflow browser in ComfyUI to select an included example.

## Before you deploy

These are tested minimum configurations. Larger images, batches and additional custom nodes can require more VRAM and system RAM.

| Model profile | Tested GPU | Minimum VRAM | Minimum system RAM |
| --- | --- | ---: | ---: |
| Z-Image Turbo | RTX 3090 or RTX A5000 | 20 GB | 50 GB |
| ERNIE-Image | RTX A4500 | 20 GB | 50 GB |
| Krea-2 fp8 | RTX A4500 | 20 GB | 65 GB |
| Krea-2 bf16 | RTX 3090 | 24 GB | 65 GB |
| FLUX.2 Klein | RTX A4500 | 20 GB | 50 GB |
| FLUX.2 Dev fp8 | RTX 3090 | 24 GB | 50 GB |
| FLUX.2 Dev bf16 | RTX 6000 Ada | 44 GB | 80 GB |
| Qwen-Image fp8 | RTX A5000 or RTX 3090 | 24 GB | 45 GB |
| Qwen-Image bf16 | RTX A6000 | 44 GB | 65 GB |
| Qwen-Image-Edit fp8 | RTX A5000 or RTX 3090 | 24 GB | 45 GB |
| Qwen-Image-Edit bf16 | RTX A5000 | 24 GB | 65 GB |

See [image-model hardware requirements](ComfyUI_image_hardware.md) for the complete tested list.

### Storage checklist

| Model family | Minimum persistent volume at `/workspace` |
| --- | ---: |
| Z-Image | 50 GB |
| ERNIE-Image | 50 GB |
| Krea-2 fp8 / bf16 | 50 GB / 60 GB |
| FLUX fp8 / bf16 | 75 GB / 90 GB |
| Qwen-Image | 70 GB |

Keep at least **15 GB** of pod storage in addition to the persistent volume. Do not reduce the template defaults unless you know the complete model footprint.

### Optional credentials

- Set `PASSWORD` if you want a fixed Code-Server password.
- Add `HF_TOKEN` when a gated Hugging Face model or an additional private model requires it.
- Add `CIVITAI_TOKEN` only when downloading resources from CivitAI.

See [RunPod configuration](RunPod_configuration.md) for all supported environment variables and secret names.

<a id="license-note-on-flux2-klein-9b"></a>

## FLUX.2 Klein 9B license

The FLUX.2 Klein 9B weights are released under the [FLUX Non-Commercial License](https://huggingface.co/black-forest-labs/FLUX.2-klein-9B/blob/main/LICENSE.md). Local use of the model is limited to the non-commercial purposes defined in that license; commercial use of the local weights requires a separate license from Black Forest Labs. Review the license for the separate conditions that apply to generated outputs.

Before starting a template that downloads the 9B model:

1. Accept access to the distilled and/or base model on Hugging Face.
2. Create a Hugging Face token with the required read access.
3. Add that token to the RunPod template as the `HF_TOKEN` secret.
4. Deploy the pod and confirm in the logs that the model download succeeds.

Follow the [FLUX.2 Klein 9B access guide](ComfyUI_image_hf_gated.md) for the model links and manual download commands.

## Deploy and connect

1. Open the deployment link for your chosen model.
2. Choose an available GPU that meets its minimum VRAM requirement.
3. Confirm the system RAM, pod storage and persistent volume.
4. Add any required RunPod secrets or environment variables.
5. Click **Deploy Pod**.
6. Open the pod logs and wait for the final ready message. Initial startup can take several minutes while the container and models download.
7. Expand the pod, select **Connect**, and open **ComfyUI** under **HTTP Services**.

For screenshots, normal startup checkpoints and troubleshooting, follow the full [RunPod pod deployment guide](Runpod_pod_deployment.md).

<a id="container-date-tags"></a>

## Container date tags

RunPod templates use dated container tags. Keep the tag supplied by the template unless you are deliberately testing another build. Different model templates can remain on different validated tags when a newer container has not yet been tested with every model family.

<a id="tutorial"></a>

## Continue after deployment

- [Connect to the pod and run your first workflow](ComfyUI_tutorial.md#connecting-to-your-pod)
- [Choose an included image workflow](ComfyUI_image.md#choose-a-workflow)

<a id="hardware-requirements-for-running-templates-on-runpod"></a>
<a id="configuration"></a>

## Reference

| Topic | Guide |
| --- | --- |
| GPU, RAM and storage requirements | [Image-model hardware requirements](ComfyUI_image_hardware.md) |
| Environment variables and network services | [RunPod configuration](RunPod_configuration.md) |
| Pod startup and troubleshooting | [RunPod pod deployment](Runpod_pod_deployment.md) |
| Model documentation and upstream resources | [Image-model resources](ComfyUI_image_resources.md) |
