[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-wan2)](https://hub.docker.com/r/ls250824/run-comfyui-wan2)

# WAN 2.x inference with ComfyUI

Run **WAN 2.x video generation and motion-transfer models** in ComfyUI on RunPod. The template provisions the models, LoRAs, custom nodes and example workflows needed for image-to-video generation and longer motion-transfer workflows.

## What to expect

The template is intended for users who want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens and file management is helpful.

<a id="when-to-use-this-template"></a>
<a id="purpose-of-this-pod"></a>

The pod is an experimental workspace for video creators who want to combine generation models, editing models, LoRAs and custom nodes in open and flexible creative pipelines. It supports video generation, motion transfer, prompt enhancement and long-video workflows.

The approach is aligned with the open-model discussion in Eric Hartford's [Uncensored Models](https://erichartford.com/uncensored-models): local and open AI systems give advanced users more ownership, control and composability. The pod is a technical workspace for responsible use rather than a content platform or safety policy.

<a id="features"></a>
<a id="built-in-authentication"></a>

### Included features

- Automatic model and LoRA provisioning through environment variables.
- Ready-to-use workflows for video generation and enhancement.
- CUDA 12.8 with compiled attention and GPU acceleration.
- Native ComfyUI and ComfyUI-WanVideoWrapper workflows.
- Latent previews enabled for samplers.
- LoRA Manager and pre-installed custom nodes.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.

<a id="deployment-on-runpod"></a>
<a id="tutorial"></a>

## RunPod deployment

**Start here:** [Deploy and start the WAN template on RunPod](ComfyUI_WAN_deployment.md).

Once the pod is running, use the workflow examples below to choose what you want to create. Follow the [ComfyUI tutorial](ComfyUI_tutorial.md) for the steps from opening ComfyUI to running your first workflow.

## Choose a workflow

| Goal | Input | Recommended workflow | Go to |
| --- | --- | --- | --- |
| Generate a longer video from a still image | Image and prompt | WAN 2.2 image-to-video | [Workflow](#wan-22-image-to-video) |
| Transfer motion from a source video | Image, source video and prompt | SCAIL-2 motion transfer | [Workflow](#scail-2-motion-transfer) |

<a id="example-workflows"></a>

## Standard workflows

<a id="wan-22-i2v-long-video"></a>

### WAN 2.2 image-to-video

Use this workflow to animate a still image and extend the result into a longer video.

<details>
<summary><strong>View the WAN 2.2 image-to-video workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-WAN.jpg" alt="WAN 2.2 image-to-video workflow for longer video generation" style="width: 100%; height: auto;">

</details>

## Advanced workflows and tools

<a id="scail-2-i2v-long-video-motion-transfer"></a>

### SCAIL-2 motion transfer

Use SCAIL-2 to apply movement from a source video to an image while generating a longer sequence.

<details>
<summary><strong>View the SCAIL-2 motion-transfer workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-scail2.jpg" alt="SCAIL-2 image-to-video workflow for long-video motion transfer" style="width: 100%; height: auto;">

</details>

## Hardware output comparison

These screenshots show the WAN workflows running with native ComfyUI and ComfyUI-WanVideoWrapper configurations.

| GPU | Workflow environment | Guidance |
| --- | --- | --- |
| L40S | Native ComfyUI | Suited to the higher-memory WAN workflows |
| A40 | ComfyUI-WanVideoWrapper | Available with resolution, duration and RAM limitations |

<a id="pod-running-on-l40s"></a>
<a id="pod-running-on-a40"></a>

<details>
<summary><strong>View the hardware comparison screenshots</strong></summary>

<p><strong>WAN running on an L40S with native ComfyUI</strong></p>
<img loading="lazy" src="../images/runpod.jpg" alt="WAN workflow running on an L40S with native ComfyUI" style="width: 100%; height: auto;">

<p><strong>WAN running on an A40 with ComfyUI-WanVideoWrapper</strong></p>
<img loading="lazy" src="../images/runpod_A40_wrapper.jpg" alt="WAN workflow running on an A40 with ComfyUI-WanVideoWrapper" style="width: 100%; height: auto;">

</details>

## More information

- [Environment configuration](RunPod_configuration.md)
- [Hardware guidance](ComfyUI_WAN_hardware.md)
- [Image setup](ComfyUI_WAN_image_setup.md)
- [Custom nodes](ComfyUI_WAN_custom_nodes.md)
- [Resources](ComfyUI_WAN_resources.md)
- [Updates](ComfyUI_WAN_update.md)
