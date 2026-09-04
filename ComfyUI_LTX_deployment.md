<a id="template-deployment-runpod"></a>

# Deploy LTX 2.x on RunPod

Use this page to choose an LTX template, deploy it on a suitable NVIDIA GPU and open ComfyUI. Both templates support video and audio generation from text, images or video; the main choice is between the newer LTX-2.5 model chain and the established LTX-2.3 workflows.

## Quick recommendation

- Start with **LTX-2.5 INT8 ConvRot** for new text-to-video or image-to-video projects.
- Choose **LTX-2.3 BF16/FP8** for the included DWPose and SDPose video-to-video workflows or when you need the documented LTX-2.3 precision profiles.

1. Choose a [template](#choose-a-template).
2. Check its [hardware and storage requirements](#before-you-deploy).
3. Complete the [LTX-2.5 model-access step](#ltx-25-model-access) when using gated official files.
4. Open the RunPod link and configure the pod.
5. Wait until the container log reports that the pod is ready.
6. Open **Connect → HTTP Services → ComfyUI (port 8188)**.

<a id="template"></a>

## Choose a template

| Template | Included generation modes | Choose it when | RunPod |
| --- | --- | --- | --- |
| **LTX-2.5 Dev INT8 ConvRot** | Text-to-video, image-to-video, video-to-video and video transition | You want the newer LTX-2.5 chain with INT8 ConvRot models and GPU-based profile selection | [**Deploy LTX-2.5 →**](https://console.runpod.io/deploy?template=ka3hvli4kf&ref=se4tkc5o) |
| **LTX-2.3 Dev BF16/FP8** | Text-to-video, image-to-video, video-to-video and video transition | You want the existing BF16/FP8 profiles or pose-transfer workflows | [**Deploy LTX-2.3 →**](https://console.runpod.io/deploy?template=p4f6rm9tb4&ref=se4tkc5o) |

After deployment, use the ComfyUI workflow browser to select an included example. LTX-2.5 provides standard text-to-video and image-to-video workflows; LTX-2.3 includes DWPose and SDPose video-to-video transfer examples.

## Before you deploy

Select a GPU listing with a valid **region ID**. Hosts without a region ID have been unreliable in the documented RunPod tests.

### LTX-2.5 provisioning targets

The following values are conservative targets based on model size and ComfyUI offloading. They are not universal benchmarked minimums.

| Profile | Typical GPU | VRAM | System RAM |
| --- | --- | ---: | ---: |
| INT8 ConvRot transformer and encoder | RTX 3090, RTX 4090 or RTX 5090 | 24 GB minimum; 32 GB preferred | 64 GB minimum; 80 GB recommended |
| INT8 ConvRot transformer with BF16 encoder | L40S, RTX A6000 or RTX 6000 Ada | 48 GB | 80 GB minimum; 96 GB recommended |
| High-memory profile | A100/H100 80 GB or RTX PRO 6000 96 GB | 80 GB or more | 96 GB minimum; 128 GB recommended |

The supplied LTX-2.5 profile uses a 40 GB VRAM threshold. GPUs with more than 40 GB receive the high-VRAM model set; GPUs at or below it receive the low-VRAM model set.

Allow at least **120 GB** of persistent storage at `/workspace` for ComfyUI, one complete model profile, custom nodes and a modest amount of output. Longer or higher-resolution videos require more space.

### LTX-2.3 tested minimums

| Precision | Tested GPU | Minimum VRAM | Minimum system RAM | Tested output |
| --- | --- | ---: | ---: | --- |
| FP8 mixed | RTX A5000 or RTX 4090 | 24 GB | 50 GB | 1280×736, 20 seconds, 24 fps |
| BF16 | L40S or RTX 6000 Ada | 45 GB | 60 GB | 1920×1088, 20 seconds, 24 fps |

Higher resolutions, longer videos, larger batches and concurrent model loading can require more VRAM, RAM and storage. See the full [LTX hardware requirements](ComfyUI_LTX_hardware.md).

### Optional credentials

- Set `PASSWORD` if you want a fixed Code-Server password.
- Add `HF_TOKEN` when downloading gated official LTX-2.5 files or private Hugging Face resources.
- Add `CIVITAI_TOKEN` only when downloading resources from CivitAI.

See [RunPod configuration](RunPod_configuration.md) for all supported environment variables and secret names.

<a id="ltx-25-model-access"></a>

## LTX-2.5 model access

The template documents a public LTX-2.5 model chain as well as optional official files from the gated [Lightricks/LTX-2.5 repository](https://huggingface.co/Lightricks/LTX-2.5). To use the gated files:

1. Sign in to Hugging Face with the account that will own the token.
2. Read the [current LTX-2.x Community License Agreement](https://github.com/Lightricks/LTX-2/blob/main/LICENSE.md).
3. Select **Agree and Access** on the model repository.
4. Create a Hugging Face read token with access to `Lightricks/LTX-2.5`.
5. Store it in a RunPod secret and reference it through `HF_TOKEN`.
6. Deploy or restart the pod and confirm in the logs that the model download succeeds.

Access is linked to the Hugging Face account that accepted the terms. A token from another account does not inherit that access. Follow the [LTX-2.5 access guide](ComfyUI_LTX_25_hf_gated.md) for secret examples, verification and manual downloads.

## Deploy and connect

1. Open the deployment link for your chosen LTX version.
2. Choose an available GPU that matches a documented profile and has a region ID.
3. Confirm the system RAM and persistent `/workspace` storage.
4. Add any required RunPod secrets or environment variables.
5. Click **Deploy Pod**.
6. Open the pod logs and wait for the final ready message. Initial startup can take several minutes while the container and models download.
7. Expand the pod, select **Connect**, and open **ComfyUI** under **HTTP Services**.

For screenshots, normal startup checkpoints and troubleshooting, follow the full [RunPod pod deployment guide](Runpod_pod_deployment.md).

<a id="container-date-tags"></a>

## Container date tags

RunPod templates use dated container tags. Keep the tag supplied by the template unless you are deliberately testing another build. LTX-2.5 and LTX-2.3 can remain on different validated tags when a newer container has not yet been tested with both model chains.

<a id="tutorial"></a>

## Continue after deployment

- [Connect to the pod and run your first workflow](ComfyUI_tutorial.md#connecting-to-your-pod)
- [Choose an included LTX workflow](ComfyUI_LTX.md#choose-a-workflow)

<a id="hardware-requirements"></a>
<a id="configuration"></a>

## Reference

| Topic | Guide |
| --- | --- |
| GPU, RAM and storage requirements | [LTX hardware requirements](ComfyUI_LTX_hardware.md) |
| Gated LTX-2.5 model access | [LTX-2.5 access guide](ComfyUI_LTX_25_hf_gated.md) |
| Environment variables and network services | [RunPod configuration](RunPod_configuration.md) |
| Pod startup and troubleshooting | [RunPod pod deployment](Runpod_pod_deployment.md) |
