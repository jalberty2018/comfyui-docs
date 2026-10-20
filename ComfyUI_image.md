[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image)](https://hub.docker.com/r/ls250824/run-comfyui-image) [![Docker Image2 Version](https://img.shields.io/docker/v/ls250824/run-comfyui-image2)](https://hub.docker.com/r/ls250824/run-comfyui-image2)

# Image inference with ComfyUI

Run **image generation and image editing models** in ComfyUI on RunPod. The templates provision the models, LoRAs, custom nodes and example workflows needed for:

- MOSS-image
- Z-Image
- FLUX.2 Dev
- FLUX.2 Klein 9B
- FLUX 3 Image klein
- JoyCaption
- Krea-2
- SenseNova U1.5
- Qwen-Image/Edit
- Qwen-Image 2.1

## What to expect

These templates are intended for users who want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens and file management is helpful.

<a id="when-to-use-this-template"></a>
<a id="purpose-of-this-pod"></a>

The pod is an experimental workspace for image creators who want to combine generation models, editing models, LoRAs and custom nodes in open and flexible creative pipelines. It supports image generation, identity-aware editing, prompt enhancement, captioning and controlled image creation.

These pods use where possible heretic/uncensored models and custom_nodes to reduce saveguards and refusals

The approach is aligned with the open-model discussion in Eric Hartford's [Uncensored Models](https://erichartford.com/uncensored-models): local and open AI systems give advanced users more ownership, control and composability. The pods are a technical workspace for responsible use rather than a content platform or safety policy.

<a id="features"></a>
<a id="built-in-authentication"></a>

### Included features

- Automatic model selection dependant on selected hardware.
- Ready-to-use workflows for image generation, editing and enhancement.
- CUDA 12.8/13.x with compiled attention and GPU acceleration.
- LoRA Manager and pre-installed custom nodes.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.
- Prompt enhancers working with gpu accelerated native llama-cpp or llama-cpp-python.

<a id="deployment-on-runpod"></a>
<a id="tutorial"></a>

## RunPod deployment

**Start here:** [Choose, deploy and start an image template on RunPod](ComfyUI_image_deployment.md).

Once the pod is running, use the workflow examples below to choose what you want to create. Follow the [ComfyUI tutorial](ComfyUI_tutorial.md) for the steps from opening ComfyUI to running your first workflow.

## MOSS-Image

### Example images

**ComfyUI t2i with prompt enhancer**

<img loading="lazy" src="../images/Image-MOSS-t2i.jpg" alt="t2i" style="width: 40%; height: auto;">

**ComfyUI t2i with vlm reference image**

<img loading="lazy" src="../images/Image_MOSS_vlm_reference.jpg" alt="t2i vlm" style="width: 60%; height: auto;">

## Flux 3 image klein

### Example images

**t2v with prompt expander (VLM)**

<img loading="lazy" src="../images/Image_Flux_3_klein_t2v.jpg" alt="t2i" style="width: 40%; height: auto;">

**ComfyUI t2i with vlm reference image**

<img loading="lazy" src="../images/comfyui-docs/images/Image_Flux_3_klein_composition.jpg" alt="i2I" style="width: 60%; height: auto;">

## Krea-2

### Example images

**t2i ostris controlnet**

<img loading="lazy" src="../images/Image_Krea2_controlnet.jpg" alt="t2i ostris controlnet" style="width: 100%; height: auto;">

**t2i Qwen text/image conditioning**

<img loading="lazy" src="../images/Image_Krea2_boy_barbie.jpg" alt="t2i conditioning" style="width: 60%; height: auto;">

**Krea 2 Identity Edit V1**

<img loading="lazy" src="../images/Image_Krea2_girl_cocktail.jpg" alt="t2i edentity edit" style="width: 60%; height: auto;">

**Krea 2 Identity Edit V2**

<img loading="lazy" src="../images/Image_krea2_identity_edit.jpg" alt="identitity edit v2" style="width: 60%; height: auto;">

**Krea 2 General Edit V2**

<img loading="lazy" src="../images/Image_krea2_general_edit.jpg" alt="general edit v2" style="width: 60%; height: auto;">

<img loading="lazy" src="../images/image_krea2_general_compose.jpg" alt="compose edit v2" style="width: 60%; height: auto;">

### Identity workflows

Use these image-to-image workflows to transfer, edit or compose identities while retaining control over the target image.

<a id="example-i2i-workflow-krea-2-identity-transfer"></a>
<details>
<summary><strong>View the Krea-2 identity transfer workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-identity.jpg" alt="Krea-2 identity transfer workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-identity-edit-loop"></a>
<details>
<summary><strong>View the Krea-2 identity edit loop</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-edit.jpg" alt="Krea-2 identity edit loop workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-identity-composition"></a>
<details>
<summary><strong>View the Krea-2 identity composition workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-composition.jpg" alt="Krea-2 identity composition workflow" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-krea-2-ostris-edit"></a>
<details>
<summary><strong>View the Krea-2 Ostris edit workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-ostris-edit.jpg" alt="Krea-2 Ostris image editing workflow" style="width: 100%; height: auto;">

</details>

### text-to-image workflows

Choose a workflow based on how you want to build and condition the prompt.

| Workflow | Best suited for |
| --- | --- |
| Prompt enhancer | Expanding a short prompt before generation |
| Image conditioning without VAE encoding | Conditioning directly from a reference image |
| Artist-friendly conditioning | Creative control with an artist-oriented setup |

<a id="example-t2i-workflow-krea-2-with-prompt-enhancer"></a>
<details>
<summary><strong>View the Krea-2 prompt enhancer workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2.jpg" alt="Krea-2 text-to-image workflow with prompt enhancer" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-krea-2-with-image-conditioning-without-vae-encoding"></a>
<details>
<summary><strong>View the Krea-2 image-conditioning workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-vlm.jpg" alt="Krea-2 text-to-image workflow with image conditioning and no VAE encoding" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-krea-2-artist-friendly-conditioning"></a>
<details>
<summary><strong>View the Krea-2 artist-friendly workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-krea2-vlm-artist.jpg" alt="Krea-2 text-to-image workflow with artist-friendly conditioning" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-krea-2-controlnet"></a>
<details>
<summary><strong>View the Krea-2 ostris controlnet with 3D pose workflow</strong></summary>
s
<img loading="lazy" src="../images/workflow-example-krea2-controlnet.jpg" alt="Krea-2 text-to-image workflow controlnet" style="width: 100%; height: auto;">

</details>

### SenseNova U1.5

Use SenseNova U1.5 for text-to-image generation or image-to-image editing with the Final BF16 checkpoint and optional distilled 8-step LoRA.

<a id="example-workflow-sensenova-u15"></a>
<details>
<summary><strong>View the SenseNova U1.5 workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-sensenova-i2v.jpg" alt="SenseNova U1.5 image workflow in ComfyUI" style="width: 100%; height: auto;">

</details>

### Qwen-Image 2.1

Use Qwen-Image 2.1 for text-to-image generation and image editing, with optional prompt enhancement.

#### Example images

**t2i prompt enhancement phrase weight adjusted turbo lora**

<img loading="lazy" src="../images/Image_Qwen21_heroin_addict.jpg" alt="t2v prompt enhancement phrase weight adjusted" style="width: 50%; height: auto;">

**i2i prompt enhancement turbo lora**

<img loading="lazy" src="../images/Image_Qwen21_girl_to_heaven.jpg" alt="i2i prompt enhancement turbo lora" style="width: 50%; height: auto;">

**i2i controlnet , pose created with 3D pose custom node**

<img loading="lazy" src="../images/Image_Qwen21_controlnet.jpg" alt="i2i controlner" style="width: 100%; height: auto;">

#### Workflows included

| Workflow | Best suited for |
| --- | --- |
| `t2i` | Generating an image from a text prompt |
| `i2i` | Editing an image with text instructions |
| `t2i-prompt-enhancer` | Expanding a prompt before image generation |
| `i2i-prompt-enhancer` | Enhancing instructions before image editing |
| `i2i-controlnet` | Modify the pose of a reference inmage with 3D pose |

<a id="example-t2i-workflow-qwen-image-21-with-prompt-enhancer"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 text-to-image prompt enhancer workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-t2i-prompt-enhancer.jpg" alt="Qwen-Image 2.1 text-to-image workflow with prompt enhancer" style="width: 100%; height: auto;">

</details>

<a id="example-t2i-workflow-qwen-image-21-phrase-weights"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 text-to-image phrase weights workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-t2i-phrase.jpg" alt="Qwen-Image 2.1 text-to-image workflow with phrase weights" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-qwen-image-21-with-prompt-enhancer"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 image-edit prompt enhancer workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-i2i-prompt-enhancer.jpg" alt="Qwen-Image 2.1 image-edit workflow with prompt enhancer" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-qwen-image-21-with-prompt-enhancer-detail"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 image-edit prompt enhancer custom node</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-i2i-prompt-enhancer-node.jpg" alt="Qwen-Image 2.1 prompt enhancer custom node" style="width: 100%; height: auto;">

</details>

<a id="example-i2i-workflow-qwen-image-21-controlnet"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 controlnet workflow with 3D poser</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-i2i-controlnet.jpg" alt="Qwen-Image 2.1 prompt enhancer custom node" style="width: 100%; height: auto;">

</details>

### FLUX.2 Klein workflows

<a id="example-workflow-flux-klein-composition"></a>
<details>
<summary><strong>View the FLUX.2 Klein multiple image composition workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-FLUX-KLEIN-3.jpg" alt="FLUX.2 Klein multiple images composition workflow" style="width: 100%; height: auto;">

</details>

Use FLUX.2 Klein when generation needs to follow a control, target or reference image.

<a id="example-workflow-flux-klein-controltarget-image-generation"></a>
<details>
<summary><strong>View the FLUX.2 Klein control and target workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-FLUX-KLEIN.jpg" alt="FLUX.2 Klein control and target image generation workflow" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-flux-klein-refcontrol-image-generation"></a>
<details>
<summary><strong>View the FLUX.2 Klein RefControl workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-FLUX-KLEIN-2.jpg" alt="FLUX.2 Klein RefControl image generation workflow" style="width: 100%; height: auto;">

</details>

### Multiple-angle workflows

Generate several viewing angles with Qwen Image 2.1 , Qwen-Image-Edit or FLUX.2 Dev.

<a id="example-i2i-workflow-qwen-image-21-multiple-angles"></a>
<details>
<summary><strong>View the Qwen-Image 2.1 mutiple angle workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-qwen-image-21-i2i-multiple-angle.jpg" alt="Qwen-Image 2.1 multiple angle" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-qwen-image-edit-multiple-angles"></a>
<details>
<summary><strong>View the Qwen-Image-Edit multiple-angle workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-QWEN-EDIT-CAMERA.jpg" alt="Qwen-Image-Edit workflow for multiple camera angles" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-flux2-dev-multiple-angles"></a>
<details>
<summary><strong>View the FLUX.2 Dev multiple-angle workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-FLUX2-CAMERA.jpg" alt="FLUX.2 Dev workflow for multiple camera angles" style="width: 100%; height: auto;">

</details>

<a id="example-workflow-zib-zit"></a>

### ZIB-ZIT

Use the ZIB-ZIT workflow for text-to-image generation with the Z-Image model family.

<details>
<summary><strong>View the ZIB-ZIT workflow</strong></summary>

<img loading="lazy" src="../images/workflow-example-ZIB-ZIT.jpg" alt="ZIB-ZIT image generation workflow" style="width: 100%; height: auto;">

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
| SenseNova U1.5 | bf16 | L40S | L40S example; t2i and i2i also tested on RTX 6000 Ada |
| Qwen-Image 2.1 | INT8 ConvRot | L40S, RTX 4090,6000 PRO MiG 24 Gb | Tested with 60 GB volume storage; |

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
<a id="example-running-sensenova-u15-bf16-on-an-l40s"></a>
<a id="example-running-qwen-image-21-on-an-l40s"></a>
<a id="example-running-qwen-image-21-on-an-rtx-4090"></a>

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

<p><strong>SenseNova U1.5 bf16 on an L40S</strong></p>
<img loading="lazy" src="../images/runpod_L40S_SenseNova.jpg" alt="SenseNova U1.5 bf16 running on an L40S" style="width: 100%; height: auto;">

<p><strong>Qwen-Image 2.1 on an L40S</strong></p>
<img loading="lazy" src="../images/runpod_L40S_QWEN-Image-21.jpg" alt="Qwen-Image 2.1 running on an L40S" style="width: 100%; height: auto;">

<p><strong>Qwen-Image 2.1 on an RTX 4090</strong></p>
<img loading="lazy" src="../images/runpod_RTX4090_QWEN-Image-21.jpg" alt="Qwen-Image 2.1 running on an RTX 4090" style="width: 100%; height: auto;">

<p><strong>Qwen-Image 2.1 on an RTX PRO 6000 MiG 24Gb</strong></p>
<img loading="lazy" src="../images/runpod_RTXPRO6000MIG24_QWEN-Image-21.jpg" alt="Qwen-Image 2.1 running on an RTX PRO 6000 MiG 24 Gb" style="width: 100%; height: auto;">

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
