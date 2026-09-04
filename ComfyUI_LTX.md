[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-ltx)](https://hub.docker.com/r/ls250824/run-comfyui-ltx)

# LTX 2.x inference with ComfyUI

Run **LTX-2.x video and audio generation** in ComfyUI on RunPod. The template provisions the models, text encoders, VAEs, LoRAs, custom nodes and example workflows needed for text-to-video, image-to-video and video-to-video generation.

## What to expect

The template is intended for users who want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens and file management is helpful.

<a id="when-to-use-this-template"></a>
<a id="purpose-of-this-pod"></a>

The pod is an experimental workspace for video creators who want to combine generation models, editing models, LoRAs and custom nodes in open and flexible creative pipelines. It supports video and audio generation, pose transfer, prompt enhancement and longer video workflows.

The approach is aligned with the open-model discussion in Eric Hartford's [Uncensored Models](https://erichartford.com/uncensored-models): local and open AI systems give advanced users more ownership, control and composability. The pod is a technical workspace for responsible use rather than a content platform or safety policy.

<a id="features"></a>
<a id="built-in-authentication"></a>

### Included features

- Complete LTX-2.x model chain.
- Public ungated LTX-2.5 model chain from `comfyicu/LTX-2.5`.
- Community Heretic BF16 and INT8 ConvRot text-encoder profiles selected by GPU VRAM.
- Video and audio VAEs, spatial and temporal latent upscalers, and a duration-head patch.
- CUDA 12.8 with compiled attention and GPU acceleration.
- ComfyUI, Code Server, SSH and LoRA Manager.
- Authentication for Hugging Face and CivitAI.

<a id="deployment-on-runpod"></a>
<a id="tutorial"></a>

## RunPod deployment

**Start here:** [Deploy and start the LTX template on RunPod](ComfyUI_LTX_deployment.md).

Once the pod is running, use the workflow examples below to choose what you want to create. Follow the [ComfyUI tutorial](ComfyUI_tutorial.md) for the steps from opening ComfyUI to running your first workflow.

## Choose a workflow

| Goal | Input | Recommended workflow | Go to |
| --- | --- | --- | --- |
| Animate a still image | Image and prompt | LTX-2.5 image-to-video | [Workflow](#ltx-25-image-to-video) |
| Generate a video from a description | Text prompt | LTX-2.5 text-to-video | [Workflow](#ltx-25-text-to-video) |
| Transfer a pose from a source video | Source video and pose reference | LTX-2.3 DWPose transfer | [Workflow](#dwpose-video-to-video-transfer) |
| Transfer a pose while adjusting body proportions | Source video and pose reference | LTX-2.3 SDPose transfer | [Workflow](#sdpose-video-to-video-transfer) |

<a id="example-included-workflows"></a>

## Standard workflows

<a id="ltx-25-i2v"></a>

### LTX-2.5 image-to-video

Select the output size and frame count, enter a prompt and configure offloading for the available GPU memory.

<details>
<summary><strong>View the LTX-2.5 image-to-video workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-i2v-LTX25.jpg" alt="LTX-2.5 image-to-video workflow with frame, size, prompt and offload controls" style="width: 100%; height: auto;">

</details>

<a id="ltx-25-t2v"></a>

### LTX-2.5 text-to-video

Generate video and audio from a text description with controls for size, duration and model offloading.

<details>
<summary><strong>View the LTX-2.5 text-to-video workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-t2v-LTX25.jpg" alt="LTX-2.5 text-to-video workflow with frame, size, prompt and offload controls" style="width: 100%; height: auto;">

</details>

## Advanced workflows and tools

<a id="ltx-23-vi2v-pose-transfer-dwpose"></a>

### DWPose video-to-video transfer

Use DWPose guidance to transfer movement from a source video to the generated subject.

<details>
<summary><strong>View the LTX-2.3 DWPose transfer workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-LTX-vi2v.jpg" alt="LTX-2.3 video-to-video pose-transfer workflow using DWPose" style="width: 100%; height: auto;">

</details>

<a id="ltx-23-vi2v-pose-transfer-sdpose-body-ratio-mapper"></a>

### SDPose video-to-video transfer

Use SDPose with Body Ratio Mapper when the transferred movement also needs proportional body adjustment.

<details>
<summary><strong>View the LTX-2.3 SDPose transfer workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-LTX-vi2v-sdpose.jpg" alt="LTX-2.3 video-to-video pose-transfer workflow using SDPose and Body Ratio Mapper" style="width: 100%; height: auto;">

</details>

## Output examples

The following clips show the output of the standard LTX-2.5 workflows.

<a id="i2v-ltx25"></a>

### Image-to-video example

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_girl_drinking_cocktail_LTX25.mp4" type="video/mp4">
  </video>
</div>

<a id="t2v-ltx25"></a>

### Text-to-video example

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_girl_walking_on_beach_LTX25.mp4" type="video/mp4">
  </video>
</div>

## Hardware output comparison

These screenshots show LTX-2.5 and LTX-2.3 running with different model precisions and GPU configurations.

| Version | GPU | Precision or profile |
| --- | --- | --- |
| LTX-2.5 | L40S | INT8 ConvRot |
| LTX-2.3 | L40S | BF16 |
| LTX-2.3 | RTX 6000 Ada | BF16 |
| LTX-2.3 | RTX A5000 | FP8 |
| LTX-2.3 | RTX 4090 | FP8 |

<a id="ltx-25-pod-running-on-l40s-int8-convrot"></a>
<a id="ltx-23-pod-running-on-l40s-bf16"></a>
<a id="ltx-23-pod-running-on-rtx-6000-ada-bf16"></a>
<a id="ltx-23-pod-running-on-rtx-a5000-fp8"></a>
<a id="ltx23-pod-running-on-rtx-4090-fp8"></a>

<details>
<summary><strong>View the hardware comparison screenshots</strong></summary>

<p><strong>LTX-2.5 on an L40S with INT8 ConvRot</strong></p>
<img loading="lazy" src="../images/runpod_L40S_LTX25.jpeg" alt="LTX-2.5 running on an L40S with the INT8 ConvRot profile" style="width: 100%; height: auto;">

<p><strong>LTX-2.3 on an L40S with BF16</strong></p>
<img loading="lazy" src="../images/runpod_L40S_LTX.jpeg" alt="LTX-2.3 running on an L40S with BF16 precision" style="width: 100%; height: auto;">

<p><strong>LTX-2.3 on an RTX 6000 Ada with BF16</strong></p>
<img loading="lazy" src="../images/runpod_6000Ada_LTX.jpeg" alt="LTX-2.3 running on an RTX 6000 Ada with BF16 precision" style="width: 100%; height: auto;">

<p><strong>LTX-2.3 on an RTX A5000 with FP8</strong></p>
<img loading="lazy" src="../images/runpod_A5000_LTX.jpeg" alt="LTX-2.3 running on an RTX A5000 with FP8 precision" style="width: 100%; height: auto;">

<p><strong>LTX-2.3 on an RTX 4090 with FP8</strong></p>
<img loading="lazy" src="../images/runpod_RTX4090_LTX.jpeg" alt="LTX-2.3 running on an RTX 4090 with FP8 precision" style="width: 100%; height: auto;">

</details>

## More information

- [Environment configuration](RunPod_configuration.md)
- [Hardware guidance](ComfyUI_LTX_hardware.md)
- [Image setup](ComfyUI_LTX_image_setup.md)
- [Custom nodes](ComfyUI_LTX_custom_nodes.md)
- [Resources](ComfyUI_LTX_resources.md)
- [Updates](ComfyUI_LTX_update.md)
