# 🚀 Starting a Pod

![deployment speed 1](images/runpod_ready.jpg)
![deployment speed 2](images/runpod_ready_RTX6000PRO.jpg)
![deployment speed 3](images/runpod_ready_L40S.jpg)

- The containers are thoroughly tested before being used in the templates. However, deploying a pod can still be frustrating due to slow or overloaded hardware on RunPod, as well as limited network performance when connecting to Docker Hub or the Hugging Face Hub. The parameters below will help you identify and stop an underperforming pod. A fast GPU provides little benefit when the rest of the system cannot operate at a comparable speed. The screenshots above are examples of full deployment speeds of an excellent performing pod.

- Check [runpod uptime](https://uptime.runpod.io/) to check if there are issues for a specific regio.

## 🧩 Choose a Template

- A compatible GPU is preconfigured in each RunPod template and is marked with an asterisk (*). For a more comprehensive list of compatible GPUs, refer to the model-specific hardware sections below.

### Image templates

- [View available templates](ComfyUI_image_deployment.md)
- [Compatible GPUs](ComfyUI_image_hardware.md)

### MiniMax H3 templates

- [View available templates](ComfyUI_MiniMax_deployment.md)
- [Compatible GPUs](ComfyUI_MiniMax_hardware.md)

### WAN templates

- [View available templates](ComfyUI_WAN_deployment.md)
- [Compatible GPUs](ComfyUI_WAN_hardware.md)

### LTX templates

- [View available templates](ComfyUI_LTX_deployment.md)
- [Compatible GPUs](ComfyUI_LTX_hardware.md)

## Deploy the Pod

- The screenshow shows the New Pod deploy page (Early access features)

![Runpod_deploy](images/runpod_deploy_01.jpg)

1. Choose an available **GPU** (preferable marked with an asterisk)
2. Choose **Volume disk** (`/workspace`).
3. Enable volume encryption if desired.
4. Click **Deploy pod**.

## ⚠️ Assign enough system memory (RAM) to your pod

![Filter ram](images/filter_ram.jpg)

- For image generation, allocate at least twice as much system RAM as GPU VRAM.
- For video generation, allocate at least three times as much. 

You can set the minimum amount of RAM in RunPod's filters. For example, for image generation with an RTX 4090 (24 GB VRAM), selecting 60 GB of RAM is a reasonable choice.

## ⚠️ CUDA errors when deploying the pod

![Filter CUDA](images/filter_cuda.jpg)

- Deploy in another region.
- Change the filter to CUDA 12.8 in the RunPod console.

## 📜 Viewing System Logs

![Deployment start](images/downloading.jpg)

- Go to **Logs or Connect**.
- Loading and extracting takes around **4–10 minutes**, depending on the region.
- If the image does not begin downloading after **1 minute**, delete the pod and redeploy it in another region.
- If it keeps downloading without extracting after **3 minutes** delete the pod and redeploy it in another region.

The extraction ends with a message like this in the **Logs** section:

![Download and extraction complete](images/download_end.jpg)

## 🐳 Viewing Container Logs

![Container start](images/runpod_deploy_startscript.jpg)

### Copy ComfyUI from container to workspace

- The time required to copy ComfyUI from the container to the workspace is a useful indicator of overall system performance. Depending on the hardware, this process typically takes between **5 and 90 seconds**. If the copy operation stalls or takes longer than **120 seconds**, consider starting another pod and comparing its performance. A slow copy operation often indicates storage or system performance issues that can also cause problems when extracting models or loading them from disk into the GPU's video memory (VRAM). 

#### Example excellent performance
![good](images/runpod_deploy_comfyuionworkspace.jpg)

#### Example acceptable/slow performance
![bad](images/runpod_deploy_comfyuionworkspace_slow.jpg)

### Downloading models form huggingface hub

![huggingface download](images/runpod_deploy_hf_download.jpg)

![huggingface download2](images/runpod_deploy_hf_download2.jpg)

- Model download speeds depend on both network and storage performance. A download speed above **200 MB/s** is considered acceptable. If a download fails, allow the startup script to finish and then restart the pod so that it can download any missing models.

### When you see the final message, your pod is ready:

![Final message](images/final_log.jpg)

## Continue with the tutorials

- [ComfyUI tutorial](ComfyUI_tutorial.md#connecting-to-your-pod)
