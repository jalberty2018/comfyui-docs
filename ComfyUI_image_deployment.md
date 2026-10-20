<a id="template-deployment"></a>

# Deploy image models on RunPod

Use this page to choose an image-generation or image-editing template, deploy it on a suitable NVIDIA GPU and open ComfyUI. The templates contain different model families, so choose one based on the task you want to perform.

## Quick recommendation

### Starters

- Start with **MOSS-Image** for straightforward text-to-image generation with vlm prompt enhancement and reference support.

### Text-to-Image with identity edit possibility

- Choose **Krea-2 Base and Turbo** for identity, composition and broader image workflows, also perfect for text-to-image.

### Real image editing

- Choose **FLUX 3 Image Klein** for BBOX or reference-image workflows also provides text-to-image.
- Choose **Qwen-Image 2.1** for text-to-image generation and image editing, either with direct prompts or with optional prompt enhancement.
- Choose **FLUX.2 Klein** for control or reference-image workflows.
- Choose **Qwen-Image-Edit 2511** when an existing image is your main input and you need a more mature eco system.

### Experimental

- Choose **SenseNova U1.5** for text-to-image and image-to-image workflows.

### Choose a GPU

- Look for the starred GPUs in the RunPod selection screen: these are the recommended options for your template.
- The template automatically selects the appropriate model variant based on your GPU and its available VRAM.

### Steps for deployment

1. Choose a [template](#choose-a-template).
2. Open the RunPod deployment link and configure or use the pre-configured settings for the pod.
3. Wait until the container log reports that the pod is ready.
4. Open **Connect → HTTP Services → ComfyUI (port 8188)**.

<a id="runpod-templates"></a>

## Choose a template

| Template | Best suited to | RunPod |
| --- | --- | --- |
| **Flux 3 Image Klein** | Text-to-image and image editing with INT8 ConvRot models, Heretic text encoder and VLM prompt expander | [**Deploy Flux 3 Image Klein →**](https://console.runpod.io/hub/template/l9es28w20d?ref=se4tkc5o) |
| **MOSS-Image** | Text-to-image with qwen 3.5 vlm support | [**Deploy MOSS-Image →**](https://console.runpod.io/deploy?template=3fri17sxaa&ref=se4tkc5o) |
| **Krea-2 Base and Turbo** | Text-to-image, identity transfer, composition and image-editing workflows | [**Deploy Krea-2 →**](https://console.runpod.io/deploy?template=e2hlyrm22l&ref=se4tkc5o) |
| **SenseNova U1.5** | Text-to-image and image-to-image with the Final BF16 checkpoint and optional distilled 8-step LoRA | [**Deploy SenseNova U1.5 →**](https://console.runpod.io/hub/template/5o6lkmpk4p?ref=se4tkc5o) |
| **Qwen-Image 2.1 with prompt enhancer** | Text-to-image and image editing with the same image models plus Qwen3.5 9B prompt enhancers | [**Deploy Qwen-Image 2.1 + prompt enhancer →**](https://console.runpod.io/hub/template/g8ow1s1s0a?ref=se4tkc5o) |
| **Z-Image Turbo and Base** | General and fast text-to-image generation | [**Deploy Z-Image →**](https://console.runpod.io/deploy?template=ia5t70hfak&ref=se4tkc5o) |
| **FLUX.2 Dev** | High-quality generation and multiple-angle workflows | [**Deploy FLUX.2 Dev →**](https://console.runpod.io/deploy?template=8nl523gts5&ref=se4tkc5o) |
| **FLUX.2 Klein** | Control, target and reference-image workflows | [**Deploy FLUX.2 Klein →**](https://console.runpod.io/deploy?template=n1wa3lb44l&ref=se4tkc5o) |
| **Qwen-Image 2512** | Qwen text-to-image generation | [**Deploy Qwen-Image →**](https://console.runpod.io/hub/template/cbb50i30rx?ref=se4tkc5o) |
| **Qwen-Image-Edit 2511** | Image editing and multiple viewing angles | [**Deploy Qwen-Image-Edit →**](https://console.runpod.io/deploy?template=mxvvx0hcmp&ref=se4tkc5o) |

Each template includes workflows for its model family. After deployment, use the workflow browser in ComfyUI to select an included example.

### Optional credentials

- Set `PASSWORD` if you want a fixed Code-Server password.
- Add `HF_TOKEN` when a gated Hugging Face model or an additional private model requires it.
- Add `CIVITAI_TOKEN` only when downloading resources from CivitAI.

See [RunPod configuration](RunPod_configuration.md) for all supported environment variables and secret names.

## Deploy and connect

### Short version

1. Open the deployment link for your chosen model.
2. Choose an available GPU that meets its minimum VRAM requirement.
3. Confirm the system RAM, pod storage and persistent volume.
4. Add any required RunPod secrets or environment variables.
5. Click **Deploy Pod**.
6. Open the pod logs and wait for the final ready message. Initial startup can take several minutes while the container and models download.
7. Expand the pod, select **Connect**, and open **ComfyUI** under **HTTP Services**.

### Long version

For screenshots, normal startup checkpoints and troubleshooting, follow the full [RunPod pod deployment guide](Runpod_pod_deployment.md).

<a id="container-date-tags"></a>

## Container date tags

RunPod templates use dated container tags. Keep the tag supplied by the template unless you are deliberately testing another build. Different model templates can remain on different validated tags when a newer container has not yet been tested with every model family.

<a id="tutorial"></a>

## Continue after deployment

- [Connect to the pod and run your first workflow](ComfyUI_tutorial.md#connecting-to-your-pod)

## Reference

| Topic | Guide |
| --- | --- |
| GPU, RAM and storage requirements | [Image-model hardware requirements](ComfyUI_image_hardware.md) |
| Environment variables and network services | [RunPod configuration](RunPod_configuration.md) |
| Pod startup and troubleshooting | [RunPod pod deployment](Runpod_pod_deployment.md) |
| Model documentation and upstream resources | [Image-model resources](ComfyUI_image_resources.md) |
