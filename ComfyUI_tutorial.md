# ComfyUI on RunPod

Use this tutorial after deploying one of the ComfyUI templates. It shows the shortest route from a running pod to your first workflow, followed by optional tools for managing models, files and the pod itself.

For general RunPod concepts and connection methods, consult the official [RunPod Pod documentation](https://docs.runpod.io/pods/overview).

<a id="common-tasks"></a>

## Start here

| Task | Where to go |
| --- | --- |
| Deploy a template | [Start a pod](Runpod_pod_deployment.md) |
| Open ComfyUI | [Connect to your pod](#connecting-to-your-pod) |
| Run an included workflow | [Run your first workflow](#run-your-first-workflow) |
| Open a command line | [Web Terminal](#web-terminal) |
| Edit files in the browser | [Code-Server](#code-server-login) |
| Configure passwords and tokens | [RunPod secrets](#secrets) |
| Add models or LoRAs | [Model and LoRA management](#downloading-models-and-loras) |
| Free storage space | [Delete models and LoRAs](#deleting-models-and-loras) |
| Manage the pod or transfer files | [Pod and file management](#pod-and-file-management) |

<a id="starting-a-pod"></a>

## 1. Start the pod

If you have not deployed a pod yet, follow [Starting a Pod](Runpod_pod_deployment.md). Continue here when the container log shows the final ready message.

<a id="connecting-to-your-pod"></a>

## 2. Connect to your pod

1. Open **Pods** in the RunPod console.
2. Expand your running pod and select **Connect**.
3. Under **HTTP Services**, open **ComfyUI** on port `8188`.
4. Complete the ComfyUI login page.

| Service | Port | Use it for |
| --- | --- | --- |
| ComfyUI | `8188` | Loading and running workflows |
| Code-Server | `9000` | Editing files in a browser-based code editor |
| Web Terminal | — | Quick commands and troubleshooting |
| SSH/SCP | `22` | Persistent terminal access and file transfer |

[View the official RunPod connection options](https://docs.runpod.io/pods/connect-to-a-pod).

<details>
<summary><strong>View the RunPod HTTP Services panel</strong></summary>

<img loading="lazy" src="../images/services.jpg" alt="RunPod Connect panel with the available HTTP services" style="width: 100%; height: auto;">

</details>

<a id="comfyui"></a>
<a id="run-your-first-workflow"></a>

## 3. Run your first workflow

1. Open **ComfyUI** from the RunPod **Connect** panel.
2. Complete the login page if prompted.
3. Open the workflow browser from the left menu.
4. Select one of the workflows included with your template.
5. Review its prompt, media inputs, output size and duration settings.
6. Select **Run**.
7. Monitor GPU and system RAM usage in **Telemetry**.

The exact workflows depend on whether you deployed the Image, MiniMax, WAN or LTX template.

<details>
<summary><strong>View example workflow selections</strong></summary>

<p><strong>LTX workflow</strong></p>
<img loading="lazy" src="../images/workflow_LTX.jpg" alt="Selecting an included LTX workflow in ComfyUI" style="width: 100%; max-width: 800px; height: auto;">

<p><strong>MiniMax workflow</strong></p>
<img loading="lazy" src="../images/ai-generated-MiniMax.jpg" alt="Included MiniMax workflow in ComfyUI" style="width: 100%; max-width: 800px; height: auto;">

</details>

## Optional pod tools

Use these tools when you need terminal access, file editing or template credentials. They are not required for running an included workflow.

<a id="web-terminal"></a>

### Web Terminal

The Web Terminal is suitable for quick commands and troubleshooting. Use SSH instead for long-running processes.

1. Open **Pods** in the RunPod console.
2. Expand the pod and select **Connect**.
3. Select **Start** if the terminal is stopped.
4. Select **Open Web Terminal**.

<details>
<summary><strong>View the Web Terminal</strong></summary>

<img loading="lazy" src="../images/web-console.jpg" alt="RunPod Web Terminal open in the browser" style="width: 100%; height: auto;">

</details>

<a id="code-server-login"></a>

### Code-Server login

Open **Code-Server** under **HTTP Services** in the RunPod **Connect** panel. It uses the `PASSWORD` environment variable when one is configured.

<a id="password-set-in-the-runpod-template"></a>

**When `PASSWORD` is configured:** use that password on the Code-Server login page.

<a id="no-password-set"></a>

**When `PASSWORD` is not configured:** copy the generated password from the end of the container log, or open the Web Terminal and run:

```bash
cat /root/.config/code-server/config.yaml
```

Copy the password from the configuration file and enter it on the Code-Server login page.

<a id="information-available-in-the-pod"></a>
<details>
<summary><strong>View Code-Server login and pod information</strong></summary>

<img loading="lazy" src="../images/code-server.jpg" alt="Code-Server password login page" style="width: 100%; max-width: 800px; height: auto;">

<img loading="lazy" src="../images/code-server_info_pod.jpg" alt="Pod information available through Code-Server" style="width: 100%; height: auto;">

</details>

<a id="secrets"></a>

### RunPod secrets

Use [RunPod secrets](https://docs.runpod.io/pods/templates/secrets#manage-secrets) to store passwords and access tokens separately from the template configuration.

| Environment variable | Purpose |
| --- | --- |
| `PASSWORD` | Code-Server login |
| `CIVITAI_TOKEN` | CivitAI downloads |
| `HF_TOKEN` | Hugging Face downloads, gated repositories and uploads |

Configure required secrets before starting the pod so the startup script and tools can use them immediately.

<a id="downloading-models-and-loras"></a>

## Model and LoRA management

Choose the method that matches the source and the amount of control you need.

| Method | Best suited for |
| --- | --- |
| ComfyUI-LoRA-Manager | Browsing, downloading and inserting LoRAs through a web interface |
| Model Linker | Finding models referenced by a workflow |
| CivitAI CLI | Downloading a known CivitAI version ID |
| Hugging Face CLI | Downloading Hub files and gated models |
| Manual provisioning | Advanced template-specific model placement |

<a id="comfyui-lora-manager"></a>

### ComfyUI-LoRA-Manager

[ComfyUI-LoRA-Manager](https://github.com/willmiao/ComfyUI-Lora-Manager) provides a web interface for managing LoRAs.

<a id="launch-the-web-interface"></a>

#### Open LoRA Manager

- Open it from the ComfyUI top bar.
- Alternatively, use the URL printed near the end of the container log:

```text
https://<pod-id>-8188.proxy.runpod.net/loras
```

<a id="civitai-token"></a>

If `CIVITAI_TOKEN` was not configured before deployment, open **Preferences** in LoRA Manager and add it there.

<a id="refresh-fetch-and-download-models"></a>

#### Refresh and download

- Select **Refresh** and **Fetch** to retrieve preview images for LoRAs already stored on the pod.
- Select **Download** and enter the CivitAI model page URL, not its file-download URL.
- For `run-comfyui-wan2`, download the high-noise and low-noise LoRAs separately.

<details>
<summary><strong>View the LoRA Manager controls</strong></summary>

<img loading="lazy" src="../images/top_bar_comfyui.jpg" alt="LoRA Manager button in the ComfyUI top bar" style="width: 100%; max-width: 600px; height: auto;">

<img loading="lazy" src="../images/top_bar.jpg" alt="Refresh, fetch and download controls in LoRA Manager" style="width: 100%; height: auto;">

</details>

<a id="basic-integration"></a>

#### Add a LoRA to Image, LTX or MiniMax

For `run-comfyui-image`, `run-comfyui-ltx` and `run-comfyui-minimax`:

1. Add a **LoRA Loader (LoraManager)** node to the workflow.
2. Select the **Paper Airplane** for the LoRA in the LoRA Manager web interface.
3. Confirm that the LoRA appears in the workflow node.

<details>
<summary><strong>View the LoRA insertion controls</strong></summary>

<img loading="lazy" src="../images/send_lora.jpg" alt="Sending an image LoRA from LoRA Manager to ComfyUI" style="width: 100%; height: auto;">

<img loading="lazy" src="../images/lora_loader.jpg" alt="LoRA Loader node managed by LoRA Manager" style="width: 100%; max-width: 600px; height: auto;">

</details>

<a id="highlow-noise-model-wan-22"></a>

#### Add WAN 2.2 high-noise and low-noise LoRAs

1. Add separate high-noise and low-noise **LoRA Loader (LoraManager)** nodes.
2. Select the **Paper Airplane** for each LoRA in LoRA Manager.
3. Confirm that both LoRAs appear in their corresponding workflow nodes.

<details>
<summary><strong>View the WAN LoRA controls</strong></summary>

<img loading="lazy" src="../images/wan-load-lora.jpg" alt="Sending WAN high-noise and low-noise LoRAs to ComfyUI" style="width: 100%; max-width: 600px; height: auto;">

</details>

<a id="model-linker"></a>

### Model Linker

Model Linker tries to match models referenced by a workflow with the pod's provisioning system. It can also download missing models, so check the free space on the `/workspace` volume first.

- [Model Linker example project](https://github.com/kianxyzw/comfyui-model-linker)

<a id="example-linking-models-in-a-comfyui-template"></a>

<details>
<summary><strong>View an example of linking workflow models</strong></summary>

<img loading="lazy" src="../images/model-linker-1.jpg" alt="Model Linker workflow model discovery" style="width: 100%; max-width: 800px; height: auto;">

<img loading="lazy" src="../images/model-linker-2.jpg" alt="Model Linker model selection" style="width: 100%; max-width: 800px; height: auto;">

<img loading="lazy" src="../images/model-linker-3.jpg" alt="Model Linker provisioning result" style="width: 100%; max-width: 800px; height: auto;">

</details>

<a id="civitai-cli"></a>

### CivitAI CLI

Use this method when you know the CivitAI version ID and destination directory. Configure `CIVITAI_TOKEN` first.

```bash
civitai_com VERSION_ID /workspace/ComfyUI/models/loras/
civitai_red VERSION_ID /workspace/ComfyUI/models/loras/
```

Examples:

```bash
civitai_com 2228466 /workspace/ComfyUI/models/loras/
civitai_red 2893442 /workspace/ComfyUI/models/loras/
```

<details>
<summary><strong>View where to find a CivitAI version ID</strong></summary>

<img loading="lazy" src="../images/civitai_air.jpg" alt="CivitAI model page showing a version identifier" style="width: 100%; max-width: 600px; height: auto;">

</details>

Refresh ComfyUI by pressing **R** after downloading a model.

<a id="hugging-face-cli"></a>

### Hugging Face CLI

`HF_TOKEN` is required for gated repositories and uploads. If it was not configured as a RunPod secret, log in interactively:

```bash
hf auth login
```

Download a file to the appropriate ComfyUI model directory:

```bash
hf download ricecake/wan21NSFWClipVisionH_v10 wan21NSFWClipVisionH_v10.safetensors --local-dir /workspace/ComfyUI/models/clip_vision
```

Refresh ComfyUI by pressing **R** after the download completes.

<details>
<summary><strong>View the ComfyUI refresh control</strong></summary>

<img loading="lazy" src="../images/refresh_nodes.jpg" alt="Refreshing models and nodes in ComfyUI" style="width: 100%; max-width: 600px; height: auto;">

</details>

<a id="manual-provisioning"></a>

### Manual provisioning

Use the Web Terminal or Code-Server and follow the documentation stored inside the pod for template-specific model directories and provisioning options.

<details>
<summary><strong>View manual provisioning in Code-Server</strong></summary>

<img loading="lazy" src="../images/codeserver_manual_provisioning.jpg" alt="Manual model provisioning documentation in Code-Server" style="width: 100%; height: auto;">

</details>

<a id="deleting-models-and-loras"></a>

## Delete models and LoRAs

Deleting unused models frees space on the `/workspace` volume.

<a id="web-terminal-or-code-server"></a>

### Web Terminal or Code-Server

1. Open a terminal.
2. Run `ncdu`.
3. Navigate to the model directory and follow the on-screen instructions.

<a id="lora-manager"></a>

### LoRA Manager

1. Select the LoRA.
2. Select **Delete**.

<a id="comfyui-manager"></a>

## ComfyUI Manager

Open ComfyUI Manager from the ComfyUI top bar or menu to manage custom nodes and extensions.

<details>
<summary><strong>View the ComfyUI Manager control</strong></summary>

<img loading="lazy" src="../images/manage_extensions.jpg" alt="Manage extensions button in ComfyUI" style="width: 100%; max-width: 600px; height: auto;">

</details>

## Pod and file management

<a id="pod-management"></a>
<a id="uploading-and-downloading-files"></a>
<a id="uploading-downloading-files"></a>
<a id="advanced-features"></a>
<a id="runpod-api"></a>

| Task | Guide |
| --- | --- |
| Restart, stop or resume the pod | [Pod management](RunPod_pod_management.md) |
| Upload or download files | [File management](RunPod_file_management.md) |
| Use SSH and other advanced options | [Advanced features](RunPod_advanced_features.md) |
| Automate RunPod operations | [RunPod API](RunPod_api.md) |

## Troubleshooting

<a id="service-not-ready-or-browser-unauthorized"></a>

### Service is not ready or the browser is unauthorized

First confirm that the container log shows the final ready message. If the **Connect** buttons still do not work, use the proxy URLs printed near the end of the container log:

- ComfyUI: `https://<pod-id>-8188.proxy.runpod.net/login`
- Code-Server: `https://<pod-id>-9000.proxy.runpod.net/login`

Replace `<pod-id>` with the ID displayed in the RunPod console.

<details>
<summary><strong>View an unauthorized browser response</strong></summary>

<img loading="lazy" src="../images/edge_rights_denied.jpg" alt="Browser response when a RunPod proxy service is not authorized or ready" style="width: 100%; max-width: 600px; height: auto;">

</details>

<a id="comfyui-screen-remains-blank"></a>
<a id="code-server-screen-remains-blank"></a>

### ComfyUI or Code-Server remains blank

1. Wait one minute and try again.
2. Confirm that pod startup completed successfully.
3. Refresh the page or clear the browser cache.
4. Try another browser such as Chrome, Edge or Brave.
