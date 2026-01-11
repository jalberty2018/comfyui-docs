# 📘 Tutorial run-comfyui-wan

- This tutorial reflects my own workflow and experience on RunPod.
- Always consult the excellent official [runpod documentation](https://docs.runpod.io/pods/overview).

## 🚀 Starting a Pod

### 🧩 Choose a Template

![t2v template](images/template.jpg)

Example:
👉 [WAN 2.2 T2V (lightx2v)](https://console.runpod.io/deploy?template=qvozvvb1xd&ref=se4tkc5o)

Steps:

1. Choose a [GPU](ComfyUI_WAN_hardware.md).  
2. Edit template settings if needed.  
3. Enable volume encryption if desired.  
4. Click **Deploy On-Demand**.

### 📜 Viewing System Logs

![deployment start](images/downloading.jpg)

- Go to **Logs**.  
- Loading takes **9–15 minutes** depending on region.  
- If the image doesn’t begin downloading after **1 minute**, delete and redeploy in another region.

Ends with (example):

```txt
Digest: sha256:2b56bdd14df7af0dae7f9bd7978be9e61d791359f5ea65eedd65dcd2e16752fc
Status: Image is up to date for ls250824/run-comfyui-wan:19112025
```

### 🐳 Viewing Container Logs

```txt
ℹ️ Pod run-comfyui-wan started
ℹ️ Wait until the message 🎉 Provisioning done, ready to create AI content 🎉
```

When you see:

![final message](images/final_log.jpg)

→ Your pod is ready.

## 🔌 Connecting to Your Pod

[Docs](https://docs.runpod.io/pods/connect-to-a-pod)

![Possible http services](images/services.jpg)

### ⚠️ Not ready – Make sure your service is running!

Try to Connect with the pod-id and the port number to the proxy.
You can find the url’s at the end of the log file.

- ComfyUI: `https:<pod-id>-8188.proxy.runpod.net/` 
- Code-Server: `https:<pod-id>-9000.proxy.runpod.net/` 

### 🎨 ComfyUI

1. Select tab **Connect** → **ComfyUI**
2. Set username/password
3. Load a workflow  
4. Press **Run**  
5. Monitor GPU/RAM via **Telemetry**

![Select Workflow template (use wrapper if deployed on A40)](images/comfyui-template.jpg){ width="500" }

![Select number frames, size , prompt and offload](images/ai-generated.jpg)

### ⚠️ ComfyUI's screen remains blank

- Wait one minute and try again.
- Restart your browser and/or clear cache.
- Try with another browser (brave, chrome, edge).

## 💻 Web Terminal

![Web Terminal](images/web-console.jpg)

- Select tab **Connect**
- Enable **web terminal**  
- Provides terminal access directly in your browser.

## 🧑‍💻 Code-Server Login

![Login without password variable set](images/code-server.jpg){ width="500" }

### No "PASSWORD" set

- Copy the password displayed at the end of the container log file of the Runpod console or open the web terminal and enter.

```bash
cat /root/.config/code-server/config.yaml
```

Copy the password → log in via the Code-Server service on tab **Connect**.

### Information in pod available

![Code-Server](images/code-server-2.jpg)

### ⚠️ Code-Server's screen remains blank

- Wait one minute and try again.
- Restart your browser and/or clear cache.
- Try another browser (brave, chrome, edge).

### "PASSWORD" set as env in Runpod template

Log in via the Code-Server service on tab **Connect**.

## 🔐 Secrets

[Docs](https://docs.runpod.io/pods/templates/secrets#manage-secrets)

Useful secrets:

- `PASSWORD`
- `CIVITAI_TOKEN`
- `HF_TOKEN`

## 📥 Downloading Models and LoRAs

From web terminal or Code-Server.

### 🧩 CivitAI

If no "CIVITAI_TOKEN" was set, create and use a free token from the civitai website.

![Batch download](images/civitai_batch.jpg)

```bash
export CIVITAI_TOKEN="xxxxx"
civitai “<download-link-on-civitai>” /workspace/ComfyUI/models/<directory>
civitai --file batch.txt
```

Download for example [CivitAI](https://civitai.com/models/2071400?modelVersionId=2344329)

```bash
civitai "https://civitai.com/api/download/models/2377549?type=Model&format=SafeTensor" /workspace/ComfyUI/models/loras/
civitai "https://civitai.com/api/download/models/2377566?type=Model&format=SafeTensor" /workspace/ComfyUI/models/loras/
```

![Refresh](images/refresh_nodes.jpg){ width="300" }

Refresh ComfyUI using pressing key **r**.

### ☁️ HuggingFace

"HF_TOKEN" is mandatory but needed for gated sites or upload.

Login:

```bash
hf auth login --token xxxxx
```

or set token:

```bash
export HF_TOKEN="xxxxx"
```

Download example from [Huggingface](https://huggingface.co/ricecake/wan21NSFWClipVisionH_v10/tree/main).

```bash
hf download ricecake/wan21NSFWClipVisionH_v10 wan21NSFWClipVisionH_v10.safetensors --local-dir /workspace/ComfyUI/models/clip_vision
```

Refresh ComfyUI pressing key **r**.

## 🧩 ComfyUI-manager

- Topbar or menu

![manage_extensions](images/manage_extensions.jpg){ width="300" }

## 🧩 Restart pod

- ⚠️ To restart ComfyUI restart the pod from runpod’s console (no information loss).

![Restart_pod](images/restart_pod.jpg){ width="300" }

## 🧩 Stop and restart a pod

- No information loss as ComfyUI is copied to the /workspace volume.
- Use this option to pause your pod.

### ⚠️ Be aware that it is possible that no GPU is available when you restart the pod.

- Before stopping the pod copy your creations to cloud/local.
- You can still access to pod from the console (0.5 vCPU and little memory).

## 🔄 Uploading & Downloading Files

### ☁️ Cloud Sync

- [Docs](https://docs.runpod.io/pods/storage/cloud-sync)

#### Free dropbox

![Cloud sync](images/cloud-sync.jpg){ width="400" }

- Reliable and fast upload and download for large files.
- Go to [Dropbox developers](https://www.dropbox.com/developers)
- **Create an app** to connect with runpod.io.

### 📦 runpodctl  

- [Docs](https://docs.runpod.io/runpodctl/overview)

#### Speed

- **Fine** for **downloading** files from your pod.
- **Problematic** for **uploading large files** to your pod with slow connections (timeouts).
- Perfect for transfering files between pods.

#### Installation

- You need to install a client on your local computer.
- You do **not** need an api key to upload/download to/from your pod.

## 🔧 Advanced Features

### 🔐 SSH / SCP / SFTP

[Docs](https://docs.runpod.io/pods/configuration/use-ssh).

#### Key generation
- Linux has ssh-keygen already installed to generate keys.
- Windows install [Git](https://git-scm.com/install/windows) to get ssh-keygen.
- Put your **public key** on runpod.io keep your **private key** on your local computer.

#### Apps.

- Use [Shellfish](https://secureshellfish.app), [Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/), [Tabby terminal](https://tabby.sh/) or shell/bash.
- File transfer [Shellfish](https://secureshellfish.app) or [WinSCP](https://winscp.net/).

## 🔑 RunPod API

Useful when the web console is out (examples are outages from AWS and Cloudflare).

#### Using runpod.io API

- [Docs](https://docs.runpod.io/api-reference/overview).
- Install with "sudo apt install curl" on Ubuntu.

```bash
curl --request GET \
  --url https://rest.runpod.io/v1/pods \
  --header 'Authorization: Bearer <api-key>'

curl --request POST \
  --url https://rest.runpod.io/v1/pods/{podId}/stop \
  --header 'Authorization: Bearer <api-key>'

curl --request DELETE \
  --url https://rest.runpod.io/v1/pods/{podId} \
  --header 'Authorization: Bearer <api-key>'
```

#### Using runpodctl to start/stop your pod with your api key.

- [Docs](https://docs.runpod.io/runpodctl/overview).
- Install client on local computer.
- Use Shell/PowerShell or Bash.

```bash
runpodctl config --apiKey <YOUR_API_KEY>

runpodctl get pod --allfields

runpodctl stop pod <pod_id>

runpodctl remove pod <pod_id>
```
