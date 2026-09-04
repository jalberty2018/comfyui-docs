# Starting a Pod

Use this guide to choose a ComfyUI template, deploy it on RunPod and confirm that the pod starts correctly. Deployment usually takes several minutes because RunPod must download the container and the startup script may also download models from Docker Hub and the Hugging Face Hub.

If RunPod or a specific region appears unavailable, check the [RunPod status page](https://uptime.runpod.io/) before redeploying.

## Quick start

1. [Choose a template](#choose-a-template) for your workload.
2. [Select the GPU, RAM and workspace storage](#deploy-the-pod).
3. Click **Deploy Pod**.
4. [Monitor the startup checkpoints](#monitor-startup).
5. Wait for the final ready message.
6. [Open ComfyUI and continue with the tutorial](#continue-with-the-tutorial).

## Choose a template

A compatible GPU is preconfigured in each RunPod template and marked with an asterisk (*). Check the hardware guide before choosing another GPU.

<a id="image-templates"></a>
<a id="minimax-h3-templates"></a>
<a id="wan-templates"></a>
<a id="ltx-templates"></a>

| Workload | Use it for | Templates | Hardware guidance |
| --- | --- | --- | --- |
| Image | Image generation and editing | [View image templates](ComfyUI_image_deployment.md) | [Compatible GPUs](ComfyUI_image_hardware.md) |
| MiniMax H3 | Video and native-audio generation | [View MiniMax templates](ComfyUI_MiniMax_deployment.md) | [Compatible GPUs](ComfyUI_MiniMax_hardware.md) |
| WAN | Video generation and motion transfer | [View WAN templates](ComfyUI_WAN_deployment.md) | [Compatible GPUs](ComfyUI_WAN_hardware.md) |
| LTX | Video and audio generation | [View LTX templates](ComfyUI_LTX_deployment.md) | [Compatible GPUs](ComfyUI_LTX_hardware.md) |

## Deploy the pod

The screenshot shows RunPod's **New Pod** deployment page with the early-access interface enabled.

1. Choose an available **GPU**, preferably one marked with an asterisk (*).
2. Set a suitable minimum amount of **system RAM** in the filters.
3. Choose the **Volume Disk** mounted at `/workspace`.
4. Enable volume encryption if desired.
5. Click **Deploy Pod**.

<details>
<summary><strong>View the New Pod deployment page</strong></summary>

<img loading="lazy" src="../images/runpod_deploy_01.jpg" alt="RunPod New Pod deployment page" style="width: 100%; height: auto;">

</details>

<a id="assign-enough-system-memory-ram-to-your-pod"></a>

### Choose enough system RAM

- For image generation, allocate at least twice as much system RAM as GPU VRAM.
- For video generation, allocate at least three times as much system RAM as GPU VRAM.

For example, 60 GB of system RAM is a reasonable selection for image generation with an RTX 4090 with 24 GB of VRAM.

<details>
<summary><strong>View the RAM filter</strong></summary>

<img loading="lazy" src="../images/filter_ram.jpg" alt="RunPod filter for minimum system RAM" style="width: 100%; height: auto;">

</details>

<a id="viewing-system-logs"></a>
<a id="viewing-container-logs"></a>

## Monitor startup

Open **Logs** or **Connect** after deployment. Use these checkpoints to distinguish a normal startup from an underperforming pod.

| Phase | Healthy indication | When to investigate | Recommended action |
| --- | --- | --- | --- |
| Docker download starts | Activity begins within 1 minute | No download activity after 1 minute | Try another region |
| Docker extraction starts | Extraction begins within 3 minutes | Download continues without extraction after 3 minutes | Redeploy in another region |
| Container download and extraction | Completes in approximately 4–8 minutes | Progress is stalled or unusually slow | Compare with another pod or region |
| Copy ComfyUI to `/workspace` | Completes in 0–110 seconds | Stalls or exceeds 120 seconds | Compare storage performance with another pod |
| Model download | Sustained speed above 200 MB/s is acceptable | A model download fails | Let startup finish, then restart the pod |
| Startup complete | The final ready message appears | No final message after preceding steps complete | Review the container logs |

### Docker download and extraction

RunPod first downloads and extracts the container. This normally takes approximately **4–8 minutes**, depending on the region. The extraction phase ends with a completion message in the system logs.

<details>
<summary><strong>View a normal Docker download and extraction</strong></summary>

<p><strong>Download starts</strong></p>
<img loading="lazy" src="../images/downloading.jpg" alt="RunPod system log showing the container download starting" style="width: 100%; height: auto;">

<p><strong>Download and extraction complete</strong></p>
<img loading="lazy" src="../images/download_end.jpg" alt="RunPod system log showing completed container extraction" style="width: 100%; height: auto;">

</details>

### Container startup

After extraction, the container starts and copies ComfyUI to `/workspace`. This copy usually takes between **0 and 110 seconds**. A transfer rate of approximately **1 GB per 30 seconds** is acceptable.

<details>
<summary><strong>View normal container startup</strong></summary>

<img loading="lazy" src="../images/runpod_deploy_startscript.jpg" alt="RunPod container log showing the startup script" style="width: 100%; height: auto;">

</details>

<a id="downloading-models-form-huggingface-hub"></a>

### Downloading models from the Hugging Face Hub

Model download speeds depend on both network and storage performance. A speed above **200 MB/s** is acceptable. If a download fails, let the startup script finish and then restart the pod so that it can download any missing models.

<details>
<summary><strong>View normal model downloads</strong></summary>

<img loading="lazy" src="../images/runpod_deploy_hf_download.jpg" alt="Container log showing a model download from the Hugging Face Hub" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/runpod_deploy_hf_download2.jpg" alt="Container log showing additional model download progress" style="width: 100%; height: auto;">

</details>

<a id="when-you-see-the-final-message-your-pod-is-ready"></a>

### Pod ready

The pod is ready when the final startup message appears in the container log.

![Final container log message confirming that the pod is ready](images/final_log.jpg)

## Examples of healthy pods

These examples show pod configurations after a successful deployment. Hardware and startup times can vary by region and host.

<details>
<summary><strong>View successful pod examples</strong></summary>

<img loading="lazy" src="../images/runpod_ready.jpg" alt="Successfully deployed RunPod pod with an RTX 3090" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/runpod_ready_RTX6000PRO.jpg" alt="Successfully deployed RunPod pod with an RTX PRO 6000" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/runpod_ready_L40S.jpg" alt="Successfully deployed RunPod pod with an L40S" style="width: 100%; height: auto;">

</details>

## Troubleshooting

Use this section when a startup checkpoint is missed. The normal deployment path above remains the quickest reference when startup is progressing as expected.

<a id="cuda-errors-when-deploying-the-pod"></a>

### CUDA errors during deployment

- Try another region.
- Set the CUDA filter to **CUDA 12.8** in the RunPod console.

<details>
<summary><strong>View the CUDA filter</strong></summary>

<img loading="lazy" src="../images/filter_cuda.jpg" alt="RunPod filter set to CUDA 12.8" style="width: 100%; height: auto;">

</details>

<a id="bad-pod-not-downloading-after-1-minute"></a>

### Container download does not start

If the image does not begin downloading within **1 minute**, redeploy the pod in another region.

<details>
<summary><strong>View an example with no download activity</strong></summary>

<img loading="lazy" src="../images/runpod_deploy_docker_download_stall.jpg" alt="Underperforming RunPod pod with no container download activity" style="width: 100%; height: auto;">

</details>

<a id="bad-pod-slow-download-without-extraction-after-3-minutes"></a>

### Container does not begin extracting

If the download continues without extraction after **3 minutes**, redeploy the pod in another region.

<details>
<summary><strong>View a slow download without extraction</strong></summary>

<img loading="lazy" src="../images/runpod_deploy_docker_download_slow.jpg" alt="Underperforming RunPod pod downloading slowly without extraction" style="width: 100%; height: auto;">

</details>

<a id="copy-comfyui-from-container-to-workspace"></a>
<a id="excellent-performance"></a>
<a id="acceptable-performance"></a>
<a id="bad-pod-not-acceptable-performance"></a>

### Slow copy to the workspace

The time required to copy ComfyUI to `/workspace` is a useful indicator of storage and system performance. If the copy stalls or exceeds **120 seconds**, compare it with another pod. Slow storage can also affect model extraction and loading models into GPU memory.

<details>
<summary><strong>Compare excellent, acceptable and poor copy performance</strong></summary>

<p><strong>Excellent performance</strong></p>
<img loading="lazy" src="../images/runpod_deploy_comfyuionworkspace_perfect.jpg" alt="Excellent ComfyUI workspace copy performance" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/runpod_deploy_comfyuionworkspace.jpg" alt="Good ComfyUI workspace copy performance" style="width: 100%; height: auto;">

<p><strong>Acceptable performance</strong></p>
<img loading="lazy" src="../images/runpod_deploy_comfyuionworkspace_medium.jpg" alt="Acceptable ComfyUI workspace copy performance" style="width: 100%; height: auto;">

<p><strong>Poor performance</strong></p>
<img loading="lazy" src="../images/runpod_deploy_comfyuionworkspace_slow.jpg" alt="Poor ComfyUI workspace copy performance" style="width: 100%; height: auto;">

</details>

<a id="continue-with-the-tutorials"></a>

## Continue with the tutorial

When the final ready message appears, [connect to your pod and open ComfyUI](ComfyUI_tutorial.md#connecting-to-your-pod).
