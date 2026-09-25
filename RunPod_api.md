# 🔑 RunPod API

Useful when the web console is out (examples are outages from AWS and Cloudflare).

## Using RunPod API

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

## Using runpodctl to start/stop your pod with your API key.

- [Docs](https://docs.runpod.io/runpodctl/overview).
- Install client on local computer.
- Use PowerShell or Bash.

### Usage

```bash
runpodctl doctor

runpodctl pod list
runpodctl pod stop <pod_id>
runpodctl pod delete <pod_id>
```
