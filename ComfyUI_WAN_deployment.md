<a id="template-deployment"></a>

# Deploy WAN 2.x on RunPod

Use this page to choose a WAN video template, deploy it on a suitable NVIDIA GPU and open ComfyUI. The four templates cover text-to-video, long image-to-video, character animation and motion transfer.

## Quick recommendation

- Choose **WAN 2.2 T2V** to generate a video from a text prompt.
- Choose **WAN 2.2 I2V + I2LV SVI 2.0 PRO** to animate a still image and extend it into a longer sequence.
- Choose **WAN 2.2 Animate** for character animation or replacement driven by reference media.
- Choose **SCAIL-2 VI2V** to transfer motion from a driving video to a reference character. Its FP8 profile is the documented 24 GB VRAM option.

1. Choose a [template](#choose-a-template).
2. Check its [hardware and storage requirements](#before-you-deploy).
3. Open the RunPod deployment link and configure the pod.
4. Wait until the container log reports that the pod is ready.
5. Open **Connect → HTTP Services → ComfyUI (port 8188)**.

<a id="runpod-templates"></a>

## Choose a template

| Template | Input | Best suited to | RunPod |
| --- | --- | --- | --- |
| **WAN 2.2 T2V LightX2V** | Text prompt | Generating a video directly from a description | [**Deploy WAN T2V →**](https://console.runpod.io/deploy?template=qvozvvb1xd&ref=se4tkc5o) |
| **WAN 2.2 I2V + I2LV SVI 2.0 PRO LightX2V** | Image and prompt | Image-to-video and longer videos assembled in chunks | [**Deploy WAN I2V + SVI →**](https://console.runpod.io/deploy?template=moem21s8xb&ref=se4tkc5o) |
| **WAN 2.2 Animate LightX2V** | Character reference and driving media | Character animation and character replacement | [**Deploy WAN Animate →**](https://console.runpod.io/deploy?template=tp7gj0khyo&ref=se4tkc5o) |
| **WAN SCAIL-2 VI2V LightX2V** | Character image, driving video and optional prompt | End-to-end motion transfer, including character replacement | [**Deploy SCAIL-2 →**](https://console.runpod.io/deploy?template=9i0lkwau54&ref=se4tkc5o) |

After deployment, open the ComfyUI workflow browser and select an example included with the chosen template.

## Before you deploy

WAN workflows are sensitive to video length, resolution, chunk count and offloading. Choose the complete GPU and system-RAM profile rather than selecting a GPU based on VRAM alone.

| Workload | Tested GPU | Minimum VRAM | Minimum system RAM | Notes |
| --- | --- | ---: | ---: | --- |
| WAN 2.2 T2V or I2V, native ComfyUI | L40S or RTX 6000 Ada | 45 GB | 90 GB | Tested at 1024×768 and 122 frames |
| WAN 2.2 T2V or I2V, WanVideoWrapper | L40S or RTX 6000 Ada | 45 GB | 50 GB | Tested with offload 10 |
| SVI 2.0 PRO long video | L40S | 45 GB | 95 GB | Tested at 1072×720 with 7 × 81-frame chunks |
| WAN 2.2 T2V or I2V with limitations | A40 | 45 GB | 45 GB | WanVideoWrapper only; reduce resolution or duration |
| WAN 2.2 Animate | L40S or RTX 6000 Ada | 40 GB | 105 GB | Tested at 1024×768 with 77 chunks per sampler |
| SCAIL/SCAIL-2 FP16 | L40S or RTX 6000 Ada | 48 GB | 96 GB | Requirements vary with source length and size |
| SCAIL-2 FP8 | RTX A5000 or RTX 4090 | 24 GB | 60 GB | Lower-VRAM SCAIL-2 profile |

These values are tested minimums for the documented settings. Longer videos, additional chunks, higher resolutions and reduced offloading can require more VRAM and system RAM. See the full [WAN hardware requirements](ComfyUI_WAN_hardware.md).

### Storage checklist

- Allocate at least **90 GB** of persistent volume storage mounted at `/workspace`.
- Keep at least **15 GB** of pod storage.
- Allow additional workspace capacity for input videos, previews, chunks and generated output.
- Do not reduce the template defaults unless you know the complete model footprint.

### Optional credentials

- Set `PASSWORD` if you want a fixed Code-Server password.
- Add `HF_TOKEN` when downloading additional private or gated Hugging Face resources.
- Add `CIVITAI_TOKEN` only when downloading resources from CivitAI.

See [RunPod configuration](RunPod_configuration.md) for all supported environment variables and secret names.

## Deploy and connect

1. Open the deployment link for your chosen WAN workload.
2. Choose an available GPU that matches a complete hardware profile above.
3. Confirm the system RAM, pod storage and persistent `/workspace` volume.
4. Add any required RunPod secrets or environment variables.
5. Click **Deploy Pod**.
6. Open the pod logs and wait for the final ready message. Initial startup can take several minutes while the container and models download.
7. Expand the pod, select **Connect**, and open **ComfyUI** under **HTTP Services**.

For screenshots, normal startup checkpoints and troubleshooting, follow the full [RunPod pod deployment guide](Runpod_pod_deployment.md).

<a id="container-date-tags"></a>

## Container date tags

RunPod templates use dated container tags. Keep the tag supplied by the template unless you are deliberately testing another build. Different WAN workloads can remain on different validated tags when a newer container has not yet been tested with every model and workflow combination.

<a id="tutorial"></a>

## Continue after deployment

- [Connect to the pod and run your first workflow](ComfyUI_tutorial.md#connecting-to-your-pod)
- [Choose an included WAN workflow](ComfyUI_WAN.md#choose-a-workflow)

<a id="hardware-requirements-for-running-templates-on-runpod"></a>
<a id="configuration"></a>

## Reference

| Topic | Guide |
| --- | --- |
| GPU, RAM and storage requirements | [WAN hardware requirements](ComfyUI_WAN_hardware.md) |
| Environment variables and network services | [RunPod configuration](RunPod_configuration.md) |
| Pod startup and troubleshooting | [RunPod pod deployment](Runpod_pod_deployment.md) |
| Model documentation and upstream resources | [WAN resources](ComfyUI_WAN_resources.md) |
