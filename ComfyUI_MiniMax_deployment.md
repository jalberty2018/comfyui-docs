# Deploy MiniMax H3 on RunPod

Use this page to choose a MiniMax H3 template, deploy it on a suitable NVIDIA GPU and open ComfyUI. All four templates generate video with audio; the main choices are the workflow type and the prompt enhancer.

## Quick recommendation

If you are unsure which template to use, start with **MiniMax H3 FL2VA + Qwen**. FL2VA supports text-to-video, image-to-video and first/last-frame-to-video, while Qwen provides the faster prompt-enhancement option.

1. Check the [tested hardware profiles](#before-you-deploy).
2. Choose a [template](#choose-a-template).
3. Configure and deploy the pod.
4. Wait until the container log reports that the pod is ready.
5. Open **Connect → HTTP Services → ComfyUI (port 8188)**.

<a id="template"></a>

## Choose a template

Choose **FL2VA** for general video generation or **Ref2VA** when reference media should guide the result.

| Workflow | Use it for | Accepted inputs |
| --- | --- | --- |
| **FL2VA** | Text-to-video, image-to-video and first/last-frame-to-video | Text with an optional first frame, last frame or both |
| **Ref2VA** | Reference-guided video generation | Text with reference images, video and/or audio |

<a id="two-prompt-enhancement-options-are-available"></a>

### Choose a prompt enhancer

The enhancer expands your input prompt before generation. It is optional and does not replace the MiniMax H3 inference model.

| Enhancer | How it works | Choose it when |
| --- | --- | --- |
| **Qwen** | Uses a separate Qwen model with llama.cpp | You want faster prompt expansion and do not mind loading an additional model |
| **Tail** | Uses the MiniMax H3 text encoder | You prefer the native MiniMax prompt-enhancement path and accept slower prompt expansion |

The speed difference applies to **prompt enhancement**. Your chosen workflow, resolution, duration and GPU have the larger effect on video-generation time.

<a id="links-to-the-templates"></a>

## Deploy a template

| Template | Recommended use | RunPod |
| --- | --- | --- |
| **FL2VA + Qwen** | Best starting point for most users | [**Deploy FL2VA + Qwen →**](https://console.runpod.io/hub/template/a1nkufhzxq?ref=se4tkc5o) |
| **FL2VA + Tail** | General generation with the native MiniMax enhancer | [**Deploy FL2VA + Tail →**](https://console.runpod.io/deploy?template=v7b5g03csk&ref=se4tkc5o) |
| **Ref2VA + Qwen** | Reference-guided generation with faster prompt expansion | [**Deploy Ref2VA + Qwen →**](https://console.runpod.io/hub/template/pcsqepl6kt?ref=se4tkc5o) |
| **Ref2VA + Tail** | Reference-guided generation with the native MiniMax enhancer | [**Deploy Ref2VA + Tail →**](https://console.runpod.io/deploy?template=6qtfx7lxgc&ref=se4tkc5o) |

## Before you deploy

MiniMax H3 model files are large and depend on ComfyUI offloading. Check the selected GPU, system RAM and persistent volume before clicking **Deploy Pod**.

| GPU profile | Tested system RAM | Model profile | Suitable for |
| --- | ---: | --- | --- |
| RTX 3090/4090, 24 GB VRAM | 50 GB | Pruned INT8 ConvRot | Lowest-cost compatible option |
| RTX 5090, 32 GB VRAM | 70 GB | Pruned INT8 ConvRot | Low-VRAM Blackwell option |
| L40S, 48 GB VRAM | 80 GB | Full INT8 ConvRot | Higher quality and longer video |
| RTX PRO 6000, 96 GB VRAM | 70 GB | Full MXFP8 | Maximum tested quality and speed |

Resolution, duration and concurrent model loading can increase both VRAM and system RAM use. See [MiniMax hardware requirements](ComfyUI_MiniMax_hardware.md) for the tested output limits.

- Keep the template's persistent volume mounted at `/workspace`.
- Do not reduce the template's default storage unless you know the complete model footprint.
- Set `PASSWORD` if you want a fixed Code-Server password.
- Add `HF_TOKEN` or `CIVITAI_TOKEN` only when your additional model downloads require them.

See [RunPod configuration](RunPod_configuration.md) for all supported environment variables and secret names.

## Deploy and connect

1. Open one of the deployment links above.
2. Choose an available GPU that matches a tested profile.
3. Confirm the system RAM and persistent volume settings.
4. Add any required environment variables or RunPod secrets.
5. Click **Deploy Pod**.
6. Open the pod's logs and wait for the final ready message. Initial startup can take several minutes while the container and models download.
7. Expand the pod, select **Connect**, and open **ComfyUI** under **HTTP Services**.

For screenshots, startup checkpoints and troubleshooting, follow the full [RunPod pod deployment guide](Runpod_pod_deployment.md).

<a id="container-date-tags"></a>

## Container date tags

RunPod templates use dated container tags. Keep the tag supplied by the template unless you are deliberately testing another build. A template can remain on an earlier validated tag when a newer container has not yet been tested with that MiniMax model configuration.

<a id="tutorial"></a>

## Continue after deployment

- [Connect to the pod and run your first workflow](ComfyUI_tutorial.md#connecting-to-your-pod)
- [Choose an included MiniMax workflow](ComfyUI_MiniMax.md#choose-a-workflow)

<a id="hardware-requirements"></a>
<a id="configuration"></a>

## Reference

| Topic | Guide |
| --- | --- |
| Hardware and tested output limits | [MiniMax hardware requirements](ComfyUI_MiniMax_hardware.md) |
| Environment variables and network services | [RunPod configuration](RunPod_configuration.md) |
| Pod startup and troubleshooting | [RunPod pod deployment](Runpod_pod_deployment.md) |
