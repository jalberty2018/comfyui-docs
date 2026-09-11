[![Docker Image Version](https://img.shields.io/docker/v/ls250824/run-comfyui-minimax)](https://hub.docker.com/r/ls250824/run-comfyui-minimax)

# MiniMax inference with ComfyUI

Run **MiniMax H3 video and native-audio generation** in ComfyUI on RunPod. The template provisions the models, VAEs, custom nodes and example workflows needed for text-to-video, image-to-video, first/last-frame video and reference-to-video generation.

## What to expect

These templates are intended for users who want to run ComfyUI on RunPod and are comfortable following technical setup steps. No Linux expertise is required for normal use, but basic familiarity with RunPod pods, logs, tokens and file management is helpful.

<a id="when-to-use-this-template"></a>
<a id="purpose-of-this-pod"></a>

The pod is an experimental workspace for video creators who want to combine generation models, editing models, LoRAs and custom nodes in open and flexible creative pipelines. It supports video generation, identity-aware video generation, prompt enhancement and long video generation.

The approach is aligned with the open-model discussion in Eric Hartford's [Uncensored Models](https://erichartford.com/uncensored-models): local and open AI systems give advanced users more ownership, control and composability. The pod is a technical workspace for responsible use rather than a content platform or safety policy.

<a id="features"></a>
<a id="built-in-authentication"></a>

### Included features

- Automatic model provisioning through environment variables.
- Model downloads selected for the available VRAM and GPU architecture (Ada Lovelace or Blackwell).
- CUDA 12.8 runtime with compiled attention acceleration.
- Authentication for ComfyUI, Code Server, Hugging Face and CivitAI.
- Uncensored Heretic Qwen-VL text encoders for inference and prompt enhancement.
- LoRA Manager, installed custom nodes and accelerators.
- Ready-to-use example workflows.
- 4-step and 8-step turbo LoRAs, including LightX2V and Alibaba PDD Acc.
- Native `llama.cpp` and CUDA-enabled `llama-cpp-python` support.

## RunPod deployment

**Start here:** [Deploy and start the MiniMax template on RunPod](ComfyUI_MiniMax_deployment.md).

Once the pod is running, use the workflow examples below to choose what you want to create. Follow the [MiniMax tutorial](ComfyUI_tutorial.md) for the steps from opening ComfyUI to running your first workflow.

## Choose a workflow

Start with the generation task, then choose a standard, Turbo, LightX2V or PDD Acc variant. The JSON filenames below identify the workflows in `pod/minimax`; the guide links lead to the examples further down this page. Availability on your pod depends on the selected template and provisioned models.

### Video generation

| Goal and input | Workflow JSON | Guide |
| --- | --- | --- |
| Generate video from a text prompt | [Standard T2V] `t2v-pod.json`, [Turbo T2V] `turbo-t2v-pod.json`, [LightX2V T2V] `lightx2v-t2v-pod.json`, [PDD Acc T2V] `PDD-Acc-t2v-pod.json` | [Text-to-video](#text-to-video-t2v) |
| Animate an image or use first/last frames with a prompt | [Standard FL2V] `fl2v-pod.json`, [Turbo FL2V] `turbo-fl2v-pod.json`, [LightX2V FL2V] `lightx2v-fl2v-pod.json`, [PDD Acc FL2V] `PDD-Acc-fl2v-pod.json` | [Image-to-video](#image-to-video-i2v) |
| Guide generation with reference images, video or audio | [Standard R2V] `r2v-pod.json`, [LightX2V R2V] `lightx2v-r2v-pod.json`, [PDD Acc R2V] `PDD-Acc-r2v-pod.json` | [Reference-to-video](#reference-to-video-ref2va) |
| Continue a reference-guided scene across several shots | [LightX2V multi-shot] `lightx2v-r2v-multi-shot.json` | [Multi-shot](#multi-shot-reference-to-video) |
| Generate connected shots with context pinning | [LightX2V context pin] `lightx2v-r2v-multi-shot-context-pin.json`, [PDD Acc context pin] `PDD-Acc-r2v-multi-shot-context-pin.json` | [Multi-shot](#multi-shot-reference-to-video) |
| Use a warm-up stage for reference-guided generation | [PDD Acc R2V warm-up] `PDD-Acc-r2v-warmup-pod.json` | [Advanced reference workflow](#advanced-reference-workflow) |
| Manage generation stages in one graph | [Director] `director-pod.json` | [Director](#director-all-in-one) |

### Prompt generation and assisted workflows

Choose Qwen-VL for local prompt generation and enhancement. The integrated variants combine it with video generation; the prompt-builder variants provide tools for composing prompts and organizing reference media.

| Goal | Workflow JSON | Guide |
| --- | --- | --- |
| Generate a prompt with Qwen-VL before running a video workflow | [FL2V prompt generator] `prompt-generator-qwenvl-fl2v-pod.json`, [R2V prompt generator] `prompt-generator-qwenvl-r2v-pod.json` | [Qwen-VL prompt enhancer](#prompt-generator-using-qwen38-27b-uncensored-with-llama-cpp) |
| Enhance a prompt with Qwen-VL and generate image/first-last-frame video | [LightX2V FL2V + Qwen-VL] `lightx2v-fl2v-prompt-generator-qwenvl-pod.json`, [PDD Acc FL2V + Qwen-VL] `PDD-Acc-fl2v-prompt-generator-qwenvl-pod.json` | [Prompt tools](#prompt-tools) |
| Enhance a prompt with Qwen-VL and generate reference-guided video | [LightX2V R2V + Qwen-VL] `lightx2v-r2v-prompt-generator-qwenvl-pod.json`, [PDD Acc R2V + Qwen-VL] `PDD-Acc-r2v-prompt-generator-qwenvl-pod.json` | [Prompt tools](#prompt-tools) |
| Compose prompts and organize reference media before generation | [LightX2V R2V prompt builder] `lightx2v-r2v-prompt-builder-pod.json`, [PDD Acc R2V prompt builder] `PDD-Acc-r2v-prompt-builder-pod.json` | [Fantastic prompt builder](#fantastic-prompt-builder-media-manager) |

See also the [video and sound preview](#video-sound-preview) example for checking output before export.

## Standard workflows

<a id="ref2va"></a>
<a id="enhanced-standard-workflow-reference-to-videoaudio-ref2va"></a>

### Reference-to-video (Ref2va)

Use the enhanced Ref2va workflow to generate video and audio from a reference image while preserving the subject or visual direction.

<details>
<summary><strong>View the enhanced Ref2va workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax.jpg" alt="Enhanced MiniMax H3 Ref2va workflow" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/ai-generated-Ref2VA.jpg" alt="Detailed MiniMax H3 Ref2va workflow" style="width: 100%; height: auto;">

</details>

<a id="multi-shotmotion-context-workflow-with-3-x-10-seconds-starting-from-a-reference-image"></a>

### Multi-shot reference-to-video

Use the LightX2V multi-shot workflow for connected shots, or choose a LightX2V or PDD Acc context-pin variant. The example below shows three connected 10-second shots from one reference image; actual duration depends on workflow settings and hardware.

<details>
<summary><strong>View the multi-shot workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-multi-shot.jpg" alt="MiniMax H3 multi-shot reference-to-video workflow" style="width: 100%; height: auto;">

</details>

<a id="fl2va"></a>
<a id="enhanced-standard-workflow-image-to-videoaudio"></a>

### Image-to-video (i2v)

Use the enhanced fl2va image-to-video workflow with or without a turbo LoRA.

<details>
<summary><strong>View the image-to-video workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-i2v.jpg" alt="MiniMax H3 image-to-video workflow" style="width: 100%; height: auto;">

</details>

<a id="enhanced-standard-workflow-text-to-videoaudio"></a>

### Text-to-video (t2v)

Use the enhanced fl2va text-to-video workflow to generate video and native audio from a prompt.

<details>
<summary><strong>View the text-to-video workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-t2v.jpg" alt="MiniMax H3 text-to-video workflow" style="width: 100%; height: auto;">

</details>

## Advanced workflows and tools

<a id="custom-workflows"></a>
<a id="director-all-in-one"></a>

### Director: all-in-one

Use Director to manage generation stages in a single workflow.

<details>
<summary><strong>View the Director workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-director.jpg" alt="MiniMax H3 Director all-in-one workflow" style="width: 100%; height: auto;">

</details>

<a id="advanced-ref-workflow-with-2-samplers-warmup-and-pdd-acc-turbo-lora"></a>

### Advanced reference workflow

This workflow combines two samplers, a warm-up stage and the PDD Acc turbo LoRA.

<details>
<summary><strong>View the advanced reference workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-uncensored.jpg" alt="Advanced MiniMax H3 reference workflow with two samplers" style="width: 100%; height: auto;">

</details>

### Prompt tools

Choose a prompt workflow based on the model and interface you want to use.

| Tool | Best suited for |
| --- | --- |
| Qwen3.8-27B-Uncensored with `llama.cpp` | Local prompt generation and enhancement |
| Fantastic prompt builder and media manager | Building prompts while organizing reference media |

<a id="prompt-generator-using-uncensored-heretic-minimax-h2-qwen-vl-with-generation-tail"></a>
<details>
<summary><strong>View the optional Heretic MiniMax-H2 Qwen-VL generation-tail workflow</strong></summary>

[Workflow JSON] `prompt-generator-tail-pod.json`

<img loading="lazy" src="../images/ai-generated-MiniMax-prompt-generator.jpg" alt="MiniMax-H2 Qwen-VL prompt generator workflow" style="width: 100%; height: auto;">

</details>

<a id="prompt-generator-using-qwen38-27b-uncensored-with-llama-cpp"></a>
<details>
<summary><strong>View the Qwen3.8-27B prompt enhancer</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-prompt-enhancer.jpg" alt="Qwen3.8-27B prompt enhancer workflow using llama.cpp" style="width: 100%; height: auto;">

</details>

<a id="fantastic-prompt-builder-media-manager" style="display: block; scroll-margin-top: 5rem;"></a>
<details>
<summary><strong>View the fantastic prompt builder and media manager</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-prompt-creator.jpg" alt="MiniMax H3 prompt builder and media manager workflow" style="width: 100%; height: auto;">

</details>

<a id="video-sound-preview"></a>

### Video and sound preview

Preview generated video and audio inside the workflow before exporting the result.

<details>
<summary><strong>View the video and sound preview workflow</strong></summary>

<img loading="lazy" src="../images/ai-generated-MiniMax-preview.jpg" alt="MiniMax H3 video and sound preview workflow" style="width: 100%; height: auto;">

</details>

## Output examples

The following clips show the output of the standard and advanced workflows.

<a id="ref2va_1"></a>

### Ref2va examples

<a id="standard"></a>
**Standard reference-to-video**

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_tickling_princess.mp4" type="video/mp4">
  </video>
</div>

<a id="enhanced"></a>
**Enhanced reference-to-video**

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_girls_in_love.mp4" type="video/mp4">
  </video>
</div>

<a id="multi-shot-continuation"></a>
**Multi-shot continuation**

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_minimax_multi-shot.mp4" type="video/mp4">
  </video>
</div>

<a id="fl2va_1"></a>

### fl2va examples

<a id="i2v"></a>
**Image-to-video**

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_girl_drinking_cocktail.mp4" type="video/mp4">
  </video>
</div>

<a id="t2v"></a>
**Text-to-video**

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_girl_walking_on_beach.mp4" type="video/mp4">
  </video>
</div>

<a id="example-video-with-director"></a>

### Director example

<div style="text-align: center;">
  <video controls preload="metadata" style="width: 100%; max-width: 720px; height: auto;">
    <source src="/video/Video_minimax_slow.mp4" type="video/mp4">
  </video>
</div>

## Hardware output comparison

These examples illustrate the quality, speed and generation limits of several GPU configurations.

| GPU | Characteristic |
| --- | --- |
| L40S | Good output quality |
| RTX 5090 | Fast, with resolution and duration restrictions |
| RTX PRO 6000 | Fast, without those restrictions |
| RTX 3090/4090 | Slower, with resolution and duration restrictions |

<a id="pod-running-on-l40s-good-quality"></a>
<a id="pod-running-on-rtx-5090-fast-but-restricted-in-resolution-and-duration"></a>
<a id="pod-running-on-rtx-pro-6000-fast-and-no-restrictions"></a>
<a id="pod-running-on-rtx-30904090-slow-and-restricted-in-resolution-and-duration"></a>

<details>
<summary><strong>View the hardware comparison screenshots</strong></summary>

<p><strong>L40S — good quality</strong></p>

<img loading="lazy" src="../images/runpod_L40S_MiniMax.jpg" alt="MiniMax H3 output from a pod running on an L40S" style="width: 100%; height: auto;">

<p><strong>RTX 5090 — fast, with resolution and duration restrictions</strong></p>

<img loading="lazy" src="../images/runpod_A5000_MiniMax.jpeg" alt="MiniMax H3 output from a pod running on an RTX 5090" style="width: 100%; height: auto;">

<p><strong>RTX PRO 6000 — fast, without restrictions</strong></p>

<img loading="lazy" src="../images/runpod_RTXPRO6000_MiniMax.jpg" alt="MiniMax H3 output from a pod running on an RTX PRO 6000" style="width: 100%; height: auto;">

<p><strong>RTX 3090/4090 — slower, with resolution and duration restrictions</strong></p>

<img loading="lazy" src="../images/runpod_RTX3090_MiniMax.jpg" alt="MiniMax H3 output from a pod running on an RTX 3090" style="width: 100%; height: auto;">

</details>

## More information

- [Environment configuration](RunPod_configuration.md)
- [Hardware guidance](ComfyUI_MiniMax_hardware.md)
- [Image setup](ComfyUI_MiniMax_image_setup.md)
- [Custom nodes](ComfyUI_MiniMax_custom_nodes.md)
- [Resources](ComfyUI_MiniMax_resources.md)
- [Updates](ComfyUI_MiniMax_update.md)
