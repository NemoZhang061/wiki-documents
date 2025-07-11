

# Docker

---

This guide demonstrates how to install and configure **Docker** and **NVIDIA Container Runtime** on  Jetson Orin series devices.This setup is essential for running GPU-accelerated containers, such as Ollama, n8n, ROS, and other AI inference applications.

---

## 1. Overview

- Install Docker CE to support containerized applications
- Configure the NVIDIA runtime to enable GPU acceleration
- Set up non-root (non- `sudo` )access to Docker
- Set the NVIDIA runtime as the default for persistent usage

This guide covers：

- Docker installation
- NVIDIA runtime configuration
- Runtime validation
- Common troubleshooting


---

## 2. System Requirements

| Component       | Requirement                              |
| ---------- | -------------------------------- |
| Jetson Device  | Jetson Orin Nano / NX              |
| Operating System      | Ubuntu 20.04 or 22.04（based on JetPack） |
| Docker Version  |Docker CE ≥ 20.10  recommended           |
| NVIDIA Runtime | `nvidia-container-toolkit`       |
| CUDA  Driver    | Included in JetPack（JetPack ≥ 5.1.1 required）  |

---

## 3. Installation  Docker CE

Install Docker from the Ubuntu Official Repository:

```bash
sudo apt-get update
sudo apt-get install -y docker.io
```

> ⚠️ To install the latest Docker version, consider using the official Docker APT repository.

Verify Docker Installation：

```bash
docker --version
# Example：Docker version 20.10.17, build 100c701
```

---

## 4. Run Docker Without `sudo`（Optional）

To allow a non-root user to run Docker commands：

```bash
sudo groupadd docker         # Create the docker group (skip if it already exists)
sudo usermod -aG docker $USER
sudo systemctl restart docker
```

> 🔁 Reboot or re-login to apply group membership changes:

```bash
newgrp docker
```

---

## 5. Install NVIDIA Container Runtime

Install the runtime that enables GPU access from within containers:：

```bash
sudo apt-get install -y nvidia-container-toolkit
```

---

## 6.Configure NVIDIA Docker Runtime

### A. Register NVIDIA as a Docker Runtime

Run the following command to configure the NVIDIA runtime:

```bash
sudo nvidia-ctk runtime configure --runtime=docker
```

Ensure that the NVIDIA runtime is registered as a valid container runtime.

---

### B. Set NVIDIA as the Default Runtime

Edit the Docker daemon configuration:

```bash
sudo nano /etc/docker/daemon.json
```

Paste or confirm the following JSON content:

```json
{
  "runtimes": {
    "nvidia": {
      "path": "nvidia-container-runtime",
      "runtimeArgs": []
    }
  },
  "default-runtime": "nvidia"
}
```

Save and exit the editor.

---
### C. Restart Docker Service

Apply the configuration changes:

```bash
sudo systemctl restart docker
```

Verify that the NVIDIA runtime is active:

```bash
docker info | grep -i runtime
```

Expected output should include:

```
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: nvidia
```
---
### D. Log in to nvcr.io (NVIDIA NGC Container Registry)
  Pulling containers from nvcr.io requires a valid [NGC_API_KEY](https://org.ngc.nvidia.com/setup)
- Generate API Key
![NCG_API_KEY](/img/NGC_API_KEY.png)
- Generate Personal Key
![Generate_personal_key](/img/Generate_personal_key.png)
- docker login
  ```shell
  sudo docker login nvcr.io
  #Username:$oauthtoken
  Username: "$oauthtoken"
  #Passwordtoken
  Password: "YOUR_NGC_API_KEY"
  ```
---

## 7. GPU Access Test

Run the official CUDA container to verify GPU availability:

```bash
docker run --rm --runtime=nvidia nvcr.io/nvidia/l4t-base:r36.2.0 nvidia-smi
```

Expected Output：

- Displays CUDA version and Jetson GPU details
- Confirms that the container has successfully accessed the GPU

![docker_nvidia-smi](/img/docker_nvidia-smi.png)

**You can also use the community-maintained [jetson-containers](https://github.com/dusty-nv/jetson-containers) project to quickly set up your development environment (recommended).**

|||
|---|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **ML** | [`pytorch`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/pytorch) [`tensorflow`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/tensorflow) [`jax`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/jax) [`onnxruntime`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/onnxruntime) [`deepstream`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cv/deepstream) [`holoscan`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cv/holoscan) [`CTranslate2`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/ctranslate2) [`JupyterLab`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/code/jupyterlab)                                                                                                                                                                                                                                                                               |
| **LLM** | [`SGLang`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/sglang) [`vLLM`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/vllm) [`MLC`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/mlc) [`AWQ`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/awq) [`transformers`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/transformers) [`text-generation-webui`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/text-generation-webui) [`ollama`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/ollama) [`llama.cpp`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/llama_cpp) [`llama-factory`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/llama-factory) [`exllama`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/exllama) [`AutoGPTQ`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/local_llm) [`FlashAttention`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/attention/flash-attention) [`DeepSpeed`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/deepspeed) [`bitsandbytes`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/bitsandbytes) [`xformers`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/attention/xformers) |
| **VLM** | [`llava`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/llava) [`llama-vision`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/llama-vision) [`VILA`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/vila) [`LITA`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/lita) [`NanoLLM`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/llm/nano_llm) [`ShapeLLM`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/shape-llm) [`Prismatic`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/prismatic) [`xtuner`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vlm/xtuner)                                                                                                                                                                                                                                                                                                                |
| **VIT** | [`NanoOWL`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vit/nanoowl) [`NanoSAM`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vit/nanosam) [`Segment Anything (SAM)`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vit/sam) [`Track Anything (TAM)`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vit/tam) [`clip_trt`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vit/clip_trt)                                                                                                                                                                                                                                                                                                                                                                                                |
| **RAG** | [`llama-index`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/rag/llama-index) [`langchain`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/rag/langchain) [`jetson-copilot`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/rag/jetson-copilot) [`NanoDB`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vectordb/nanodb) [`FAISS`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vectordb/faiss) [`RAFT`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/rapids/raft)                                                                                                                                                                                                                                                                                                                                                      |
| **L4T** | [`l4t-pytorch`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/l4t/l4t-pytorch) [`l4t-tensorflow`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/l4t/l4t-tensorflow) [`l4t-ml`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/l4t/l4t-ml) [`l4t-diffusion`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/l4t/l4t-diffusion) [`l4t-text-generation`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/l4t/l4t-text-generation)                                                                                                                                                                                                                                                                                                                                                              |
| **CUDA** | [`cupy`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/numeric/cupy) [`cuda-python`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cuda/cuda-python) [`pycuda`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cuda/pycuda) [`cv-cuda`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cv/cv-cuda) [`opencv:cuda`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/cv/opencv) [`numba`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/numeric/numba)                                                                                                                                                                                                                                                                                                                                          |
| **Robotics** | [`Cosmos`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/diffusion/cosmos) [`Genesis`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/sim/genesis) [`ROS`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/robots/ros) [`LeRobot`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/robots/lerobot) [`OpenVLA`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vla/openvla) [`3D Diffusion Policy`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/diffusion/3d_diffusion_policy) [`Crossformer`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/vla/crossformer) [`MimicGen`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/sim/mimicgen) [`OpenDroneMap`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/robots/opendronemap) [`ZED`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/hardware/zed)                                                                                                                                                                                         |
| **Graphics** | [`stable-diffusion-webui`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/diffusion/stable-diffusion-webui) [`comfyui`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/diffusion/comfyui) [`nerfstudio`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/nerf/nerfstudio) [`meshlab`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/nerf/meshlab) [`pixsfm`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/nerf/pixsfm) [`gsplat`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/nerf/gsplat)                                                                                                                                                                                                                                                                                                                                    |
| **Mamba** | [`mamba`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/mamba/mamba) [`mambavision`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/mamba/mambavision) [`cobra`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/mamba/cobra) [`dimba`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/mamba/dimba) [`videomambasuite`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/ml/mamba/videomambasuite)                                                                                                                                                                                                                                                                                                                                                                                                |
| **Speech** | [`whisper`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/whisper) [`whisper_trt`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/whisper_trt) [`piper`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/piper-tts) [`riva`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/riva-client) [`audiocraft`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/audiocraft) [`voicecraft`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/voicecraft) [`xtts`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/speech/xtts)                                                                                                                                                                                                                                                                                                              |
| **Home/IoT** | [`homeassistant-core`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/smart-home/homeassistant-core) [`wyoming-whisper`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/smart-home/wyoming/wyoming-whisper) [`wyoming-openwakeword`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/smart-home/wyoming/openwakeword) [`wyoming-piper`](https://github.com/dusty-nv/jetson-containers/tree/master/packages/smart-home/wyoming/wyoming-piper)                                                                                                                                                                                                                                                                                                                                        |

---

## 8. Troubleshooting

| Issue              | Solution                               |
| ---------------- | ----------------------------------- |
|  `nvidia-smi` not found| Jetson devices use `tegrastats` instead of `nvidia-smi`        |
| No GPU access in container        | Ensure the default runtime is set to `nvidia`                 |
| Permission denied errors           | Verify that the user is in the`docker` group             |
| Container crashes            | Check logs via`journalctl -u docker.service` |

---

## 9. Appendix

### Key File Paths

| File                               | Purpose            |
| ----------------------------------- | --------------- |
| `/etc/docker/daemon.json`           | Docker runtime configuration    |
| `/usr/bin/nvidia-container-runtime` | Path to NVIDIA runtime binary|
| `~/.docker/config.json`             | (Optional) Docker user-specific config|

### References

- [Jetson Docker Runtime Official Docs](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html)
- [NVIDIA Developer Forum](https://forums.developer.nvidia.com/)
- [JetPack SDK  Download](https://developer.nvidia.com/embedded/jetpack)


