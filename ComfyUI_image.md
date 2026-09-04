[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image) [![Docker Image2 Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image2)](https://hub.docker.com/r/ls250824/run-comfyui-image2)

# Image inference with ComfyUI

Run **image generation and image editing models** in ComfyUI on RunPod. The templates provision the models, LoRAs, custom nodes and example workflows needed for Z-Image, ERNIE-Image, FLUX.2, FLUX.2 Klein, Qwen-Image, JoyCaption, Krea-2 and Qwen-Image-Edit.

## What to expect

These templates are intended for users who want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens and file management is helpful.

<a id="when-to-use-this-template"></a>
<a id="purpose-of-this-pod"></a>

The pod is an experimental workspace for image creators who want to combine generation models, editing models, LoRAs and custom nodes in open and flexible creative pipelines. It supports image generation, identity-aware editing, prompt enhancement, captioning and controlled image creation.

The approach is aligned with the open-model discussion in Eric Hartford's [Uncensored Models](https://erichartford.com/uncensored-models): local and open AI systems give advanced users more ownership, control and composability. The pod is a technical workspace for responsible use rather than a content platform or safety policy.

<a id="features"></a>
<a id="built-in-authentication"></a>

### Included features

- Automatic model and LoRA provisioning through environment variables.
- Ready-to-use workflows for image generation, editing and enhancement.
- CUDA 12.8 with compiled attention and GPU acceleration.
- Automatic selection of bf16 or fp8 models and workflows.
- LoRA Manager and pre-installed custom nodes.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.

<a id="deployment-on-runpod"></a>
<a id="tutorial"></a>

## RunPod deployment

**Start here:** [Choose, deploy and start an image template on RunPod](ComfyUI_image_deployment.md).

Once the pod is running, use the workflow examples below to choose what you want to create. Follow the [ComfyUI tutorial](ComfyUI_tutorial.md) for the steps from opening ComfyUI to running your first workflow.

## Choose a workflow

| Goal | Input | Recommended workflow | Go to |
| --- | --- | --- | --- |
| Preserve or transfer a subject's identity | Source and target images | Krea-2 identity workflows | [Workflows](#krea-2-identity-workflows) |
| Generate an image from a description | Text prompt | Krea-2 text-to-image | [Workflows](#krea-2-text-to-image-workflows) |
| Guide generation with a control or reference image | Prompt and control image | FLUX.2 Klein control | [Workflows](#flux2-klein-control-workflows) |
| Create several views of the same subject | Image and angle instructions | Multiple-angle workflows | [Workflows](#multiple-angle-workflows) |
| Generate images with ZIB-ZIT | Text prompt | ZIB-ZIT | [Workflow](#zib-zit) |
| Describe or caption an image | Image | JoyCaption | [Workflow](#joycaption) |

## Standard workflows

### Krea-2 identity workflows

Use these image-to-image workflows to transfer, edit or compose identities while retaining control over the target image.

<a id="example-i2i-workflow-krea-2-identity-transfer"></a>
<details>
<summary><strong>View the Krea-2 identity transfer workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-identity.jpg" alt="Krea-2 identity transfer workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-identity-edit-loop"></a>
<details>
<summary><strong>View the Krea-2 identity edit loop</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-edit.jpg" alt="Krea-2 identity edit loop workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-identity-composition"></a>
<details>
<summary><strong>View the Krea-2 identity composition workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-composition.jpg" alt="Krea-2 identity composition workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-ostris-edit"></a>
<details>
<summary><strong>View the Krea-2 Ostris edit workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-ostris-edit.jpg" alt="Krea-2 Ostris image editing workflow" style="width: 100%; height: auto;">

</details>

### Krea-2 text-to-image workflows

Choose a workflow based on how you want to build and condition the prompt.

| Workflow | Best suited for |
| --- | --- |
| Prompt enhancer | Expanding a short prompt before generation |
| Image conditioning without VAE encoding | Conditioning directly from a reference image |
| Artist-friendly conditioning | Creative control with an artist-oriented setup |

<a id="example-t2i-workflow-krea-2-with-prompt-enhancer"></a>
<details>
<summary><strong>View the Krea-2 prompt enhancer workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2.jpg" alt="Krea-2 text-to-image workflow with prompt enhancer" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-krea-2-with-image-conditioning-without-vae-encoding"></a>
<details>
<summary><strong>View the Krea-2 image-conditioning workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-vlm.jpg" alt="Krea-2 text-to-image workflow with image conditioning and no VAE encoding" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-krea-2-artist-friendly-conditioning"></a>
<details>
<summary><strong>View the Krea-2 artist-friendly workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-krea2-vlm-artist.jpg" alt="Krea-2 text-to-image workflow with artist-friendly conditioning" style="width: 100%; height: auto;">

</details>

## Advanced workflows and tools

### FLUX.2 Klein control workflows

Use FLUX.2 Klein when generation needs to follow a control, target or reference image.

<a id="example-workflow-flux-klein-controltarget-image-generation"></a>
<details>
<summary><strong>View the FLUX.2 Klein control and target workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-FLUX-KLEIN.jpg" alt="FLUX.2 Klein control and target image generation workflow" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-flux-klein-refcontrol-image-generation"></a>
<details>
<summary><strong>View the FLUX.2 Klein RefControl workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-FLUX-KLEIN-2.jpg" alt="FLUX.2 Klein RefControl image generation workflow" style="width: 100%; height: auto;">

</details>

### Multiple-angle workflows

Generate several viewing angles with Qwen-Image-Edit or FLUX.2 Dev.

<a id="example-workflow-qwen-image-edit-multiple-angles"></a>
<details>
<summary><strong>View the Qwen-Image-Edit multiple-angle workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-QWEN-EDIT-CAMERA.jpg" alt="Qwen-Image-Edit workflow for multiple camera angles" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-flux2-dev-multiple-angles"></a>
<details>
<summary><strong>View the FLUX.2 Dev multiple-angle workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-FLUX2-CAMERA.jpg" alt="FLUX.2 Dev workflow for multiple camera angles" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-zib-zit"></a>

### ZIB-ZIT

Use the ZIB-ZIT workflow for text-to-image generation with the Z-Image model family.

<details>
<summary><strong>View the ZIB-ZIT workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-ZIB-ZIT.jpg" alt="ZIB-ZIT image generation workflow" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-joycaption"></a>

### JoyCaption

Use JoyCaption to analyze an image and generate a detailed description or prompt.

<details>
<summary><strong>View the JoyCaption workflow</strong></summary>

<img loading="lazy" src="../images/joycaption-workflow.jpg" alt="JoyCaption image captioning workflow" style="width: 100%; height: auto;">

</details>

## Hardware output comparison

These screenshots show the workflows running with different models, precisions and GPU configurations.

| Workload | Precision | Example GPUs | Note |
| --- | --- | --- | --- |
| Z-Image | — | RTX A4500, RTX A5000, RTX 4000 Ada, RTX 3090 | Four GPU examples |
| FLUX.2 Klein 9B | — | RTX A4500 | One GPU example |
| Qwen-Image-Edit | fp8 or bf16 | RTX A5000, A40 | Two precision examples |
| FLUX.2 Dev | bf16 or fp8 | L40S, RTX A5000 | The fp8 A5000 example is slower |
| Krea-2 turbo | fp8 or bf16 | RTX A5000, RTX 4090 | Three configuration examples |

<a id="example-running-z-image-on-an-rtx-a4500"></a>
<a id="example-running-z-image-on-an-rtx-a5000"></a>
<a id="example-running-z-image-on-an-rtx-4000-ada"></a>
<a id="example-running-z-image-on-an-rtx-3090"></a>
<a id="example-running-flux2-klein-9b-on-an-rtx-a4500"></a>
<a id="example-running-qwen-image-edit-fp8-on-an-rtx-a5000"></a>
<a id="example-running-qwen-image-edit-bf16-on-an-a40"></a>
<a id="example-running-flux2-dev-bf16-on-an-l40s"></a>
<a id="example-running-flux2-dev-fp8-on-an-rtx-a5000-slow"></a>
<a id="example-running-krea-2-turbo-fp8-on-an-rtx-a5000"></a>
<a id="example-running-krea-2-turbo-bf16-on-an-rtx-a5000"></a>
<a id="example-running-krea-2-turbo-bf16-on-an-rtx-4090"></a>

<details>
<summary><strong>View the hardware comparison screenshots</strong></summary>

<p><strong>Z-Image on an RTX A4500</strong></p>
<img loading="lazy" src="../images/runpod_A4500_ZIB_ZIT.jpg" alt="Z-Image running on an RTX A4500" style="width: 100%; height: auto;">

<p><strong>Z-Image on an RTX A5000</strong></p>
<img loading="lazy" src="../images/runpod_A5000_ZIB_ZIT.jpg" alt="Z-Image running on an RTX A5000" style="width: 100%; height: auto;">

<p><strong>Z-Image on an RTX 4000 Ada</strong></p>
<img loading="lazy" src="../images/runpod_4000ADA_ZIB_ZIT.jpg" alt="Z-Image running on an RTX 4000 Ada" style="width: 100%; height: auto;">

<p><strong>Z-Image on an RTX 3090</strong></p>
<img loading="lazy" src="../images/runpod_3090_ZIB_ZIT.jpg" alt="Z-Image running on an RTX 3090" style="width: 100%; height: auto;">

<p><strong>FLUX.2 Klein 9B on an RTX A4500</strong></p>
<img loading="lazy" src="../images/runpod_FLUX_KLEIN.jpg" alt="FLUX.2 Klein 9B running on an RTX A4500" style="width: 100%; height: auto;">

<p><strong>Qwen-Image-Edit fp8 on an RTX A5000</strong></p>
<img loading="lazy" src="../images/runpod_A5000_QWEN-EDIT.jpg" alt="Qwen-Image-Edit fp8 running on an RTX A5000" style="width: 100%; height: auto;">

<p><strong>Qwen-Image-Edit bf16 on an A40</strong></p>
<img loading="lazy" src="../images/runpod_A40_QWEN-EDIT.jpg" alt="Qwen-Image-Edit bf16 running on an A40" style="width: 100%; height: auto;">

<p><strong>FLUX.2 Dev bf16 on an L40S</strong></p>
<img loading="lazy" src="../images/runpod_L40S_FLUX_2.jpg" alt="FLUX.2 Dev bf16 running on an L40S" style="width: 100%; height: auto;">

<p><strong>FLUX.2 Dev fp8 on an RTX A5000</strong></p>
<img loading="lazy" src="../images/runpod_A5000_FLUX_2.jpg" alt="FLUX.2 Dev fp8 running on an RTX A5000" style="width: 100%; height: auto;">

<p><strong>Krea-2 turbo fp8 on an RTX A5000</strong></p>
<img loading="lazy" src="../images/runpod_A5000_krea2.jpg" alt="Krea-2 turbo fp8 running on an RTX A5000" style="width: 100%; height: auto;">

<p><strong>Krea-2 turbo bf16 on an RTX A5000</strong></p>
<img loading="lazy" src="../images/runpod_A5000_krea2-bf16.jpg" alt="Krea-2 turbo bf16 running on an RTX A5000" style="width: 100%; height: auto;">

<p><strong>Krea-2 turbo bf16 on an RTX 4090</strong></p>
<img loading="lazy" src="../images/runpod_RTX490_krea2-bf16.jpg" alt="Krea-2 turbo bf16 running on an RTX 4090" style="width: 100%; height: auto;">

</details>

## More information

- [Environment configuration](RunPod_configuration.md)
- [Hardware guidance](ComfyUI_image_hardware.md)
- [Image setup](ComfyUI_image_image_setup.md)
- [Image2 setup](ComfyUI_image2_image_setup.md)
- [Image custom nodes](ComfyUI_image_custom_nodes.md)
- [Image2 custom nodes](ComfyUI_image2_custom_nodes.md)
- [Resources](ComfyUI_image_resources.md)
- [Updates](ComfyUI_image_update.md)
