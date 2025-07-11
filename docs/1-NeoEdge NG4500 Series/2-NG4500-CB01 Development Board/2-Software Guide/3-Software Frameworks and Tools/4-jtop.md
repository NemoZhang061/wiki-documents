# jtop
---
## 1. Overview

This guide describes the installation, configuration, and advanced usage of jtop on Jetson platforms. **jtop** is a Jetson-specific command-line monitoring tool developed by Raffaello Bonghi. Written in Python, it offers an htop-like interactive interface for real-time monitoring of system resources such as CPU, GPU, memory, fan speed, and power consumption.

**Key Features include：**

- Monitoring of CPU, GPU, Memory, Engines, fan
- Control NVP model, fan speed, jetson_clocks
- Importable in a python script
- Dockerizable in a container
- No super user privileges required

---

## 2. Requirements

| Component             | Requirement                              |
|------------------|--------------------------------------|
| Jetson Hardware      | Orin Nano / NX                 |
| Operating System         | Ubuntu 20.04 or 22.04(JetPack-based) |
| JetPack Version     | JetPack ≥ 5.1.1 (recommended)                |
| Python Version   | Python 3.x                            |
| pip              | Required to installed                            |
| Network        | Required to install jetson-stats                |

---

## 3. Installation

### A. Prerequisites

Ensure the system is up to date and that `pip` is installed：

```bash
sudo apt update
sudo apt install python3-pip -y
```

### B. Installing jetson-stats (includes jtop)

Using `pip` to install the `jetson-stats`：

```bash
sudo pip3 install -U jetson-stats
```

After installation, it is recommended to reboot the system or log out and re-login to apply environment changes：

```bash
sudo reboot
```

---

## 4. Launching jtop

Execute the following command to start `jtop` ：

```bash
jtop
```

![jtop](/img/jtop.gif)

The interface provides multiple views, navigable via arrow keys or the`Tab` key：

- **ALL**：Displays an overview of system metrics
- **GPU**：Monitors GPU utilization
- **CPU**：Displays CPU usage
- **MEM**：Displays memory and swap usage
- **ENG**：Reports the status of compute engines
- **CTRL**：Control of jetson_clocks、nvpmodel、fan settings
- **INFO**：System information and library versions

---

## 5. Advanced Usage

### A. Check jtop Status

To verify the integrity and status of `jtop`  and its associated components:

```bash
sudo jtop --health
```

### B. Reset Jetson Configuration

To restore key runtime parameters (including jetson_clocks, power mode, and fan settings）to default values：

```bash
jtop --restore
```

### C. Customizing Color Themes

To enable enhanced color filters for better terminal visibility：

```bash
jtop --color-filter
```

Or add the following to `.bashrc` ：

```bash
export JTOP_COLOR_FILTER=True
```

---

## 6. Python API Integration

`jtop` provides a simple Python API to access real-time system information from your Jetson device. It’s useful for monitoring, automation scripts, or integrating into your own applications:

```python
from jtop import jtop

with jtop() as jetson:
    if jetson.ok():
        print(jetson.stats)
```

---

## 7. Running jtop in Docker

To use jtop inside a Docker container：

1. Make sure jetson-stats is installed both on the host and inside the container.
2. Mount the socket file `/run/jtop.sock`when starting the container：

```bash
docker run --rm -it -v /run/jtop.sock:/run/jtop.sock rbonghi/jetson_stats:latest
```

---

## 8. Troubleshooting

| Issue                 | Solution                                        |
|----------------------|--------------------------------------------------|
| jtop fails to launch         | Ensure jetson-stats is installed and reboot the system  |
| Permission denied errors            | Run with`sudo` or verify user permissions       |
| Unable to retrieve GPU metrics    | Confirm NVIDIA drivers are installed and environment are correctly configured  |
| jtop not working in Docke| Check that `/run/jtop.sock`，is correctly mounted and jetson-stats is installed inside the container |

---

## 9. References

- Official Docs：[https://rnext.it/jetson_stats](https://rnext.it/jetson_stats)
- GitHub Repo：[https://github.com/rbonghi/jetson_stats](https://github.com/rbonghi/jetson_stats)
- NVIDIA Developer Forum：[https://forums.developer.nvidia.com](https://forums.developer.nvidia.com)

---
