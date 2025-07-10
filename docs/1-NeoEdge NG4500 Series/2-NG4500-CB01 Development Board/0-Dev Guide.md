import Link from "@docusaurus/Link";
import useBaseUrl from '@docusaurus/useBaseUrl';

## Development Kit Overview

NG4500-CB01 is a high-performance development carrier board designed for NeoEdge NG4500 series AI edge computing devices. This carrier board is suitable for NVIDIA Jetson Orin series modules (Orin Nano/NX) and is suitable for application scenarios such as machine vision, industrial automation, robotics, and AIoT.

<div style={{ display: 'grid', gridTemplateColumns: '1fr 1fr', gap: '20px', justifyContent: 'center', alignItems: 'center' }}>
  <img src={useBaseUrl('/img/Board/NG4500-CB01_1.png')} alt="front view of the carrier board" style={{ height: '300px', objectFit: 'contain', margin: '0 auto' }} />
  <img src={useBaseUrl('/img/Board/NG4500-CB01_2.png')} alt="back view of the carrier board" style={{ height: '300px', objectFit: 'contain', margin: '0 auto' }} />
</div>

## Key Features

- **Compatible with NVIDIA® Jetson Orin™  series modules**: supporting Jetson Orin Nano 4GB/8GB and Orin NX 8GB/16GB
- **Rich interfaces**:
  - Dual Gigabit Ethernet ports
  - 4×Type-A (USB 3.1) and 1×Type-C (USB 3.2)
  - RS232, RS485, CANbus
  - Digital input/output interfaces (DI/DO)
  - HDMI 4K video output
  - Audio input and output interfaces
- **Expansion capabilities**：
  - M.2 Key M PCIe 4.0 NVMe SSD interface（2280 spec.）
  - M.2 Key M PCIe 1.0 expansion interface
  - M.2 Key B interface supports 4G/5G/Wi-Fi Halow（2242/2252 spec.）
  - M.2 Key E interface supports Wi-Fi 6/Bluetooth 5.0（2230 spec.）
  - 4 lanes MIPI×2 camera interface
- **Industrial-grade design**: wide voltage input(12V-36V DC), fanless passive cooling design, operating temperature ranges from -25°C to 60°C.

## Specifications

| Category | Specifications |
|---------|------|
| Compatible modules | Jetson Orin Nano 4GB/8GB, Jetson Orin NX 8GB/16GB |
| CPU | 6/8 core Arm® Cortex® A78AE v8.2 (64-bit) |
| GPU | 512/1024 NVIDIA® CUDA® cores，16/32 Tensor cores |
| AI performance | Up to 157 INT8 TOPS（SUPER mode） |
| Memory | 4GB/8GB/16GB LPDDR5 |
| Storage expansion | Supports NVMe SSD(2280), pre-install 128GB-1TB |
|Ethernet | Gigabit Ethernet with 2×RJ45 connectors |
| Wireless Connectivity | Wi-Fi 6/Bluetooth 5.0，4G/5G/Wi-Fi Halow |
| Video | HDMI output, 2×MIPI CSI(Camera Serial Interface)|
| Serial interface | RS232, RS485, CAN |
| Power input | DC 12V-36V, peak rate 120W |
| Dimension | 160mm × 125mm × 75mm（Edge AI Box） |
| Operating system | Ubuntu Linux（JetPack 6.0+） |

## Development Resources

NG4500-CB01 carrier board provides comprehensive development resources and documentation support. The following are links to relevant development resources:

### Hardware Resources
- [Hardware components overview](./1-Hardware%20Guide/0-Components%20Overview.md) - Detailed introduction to the functions and specifications of each component of the development board.
- [Hardware connection guide](./1-Hardware%20Guide/1-Hardware%20Connection.md) - Explanation on how to use and connect the interfaces on the carrier board.

### Software Resources
- [System Flashing Guide](./2-Software%20Guide/0-System%20Flashing%20and%20Initialization.md) - Provides step-by-step instruction for flashing the Jetson module system.
- [Development Environment Set-up](./2-Software%20Guide/1-Development%20Environment%20Setup.md) - Guides on how to configure the development environment and development tools.
- [Driver Installation and Update](./2-Software%20Guide/1-Driver%20Installation%20and%20Updates/0-Interface&modules%20configure.md) - Contains driver installation instructions for various hardware interfaces.
- [Software Framework and Tools](./2-Software%20Guide/3-Software%20Frameworks%20and%20Tools/0-Docker.md) - List of supported development frameworks and tools.

### Application Development
- [DeepSeek LLM Deployment](../3-Application%20Guide/1-Deepseek-r1.md) - Tutorial guide of deploying LLMs on NG4500
- [MediaPipe Framework Deployment](../3-Application%20Guide/2-mediapipe.md) - Example of using MediaPipe to develop visual-related applications.
- [Object Detection Application](../3-Application%20Guide/3-Object%20Detection.md) - Object detection application developed based on TensorRT.

## Development Process

1. **Hardware preparation**
   - Install the Jetson Orin module to the development board
   - Connect power and peripherals (monitor, keyboard, mouse)
   - Install expansion modules (storage, communication modules, etc.) as needed

2. **System initialization**
   - Flash JetPack OS
   - Complete system initial setup
   - Install necessary drivers and updates

3. **Development environment configuration**
   - Install development tools such as CUDA, cuDNN, TensorRT
   - Configure development framework (PyTorch, TensorFlow etc.)
   - Set up the IDE and development toolchain

4. **Application development and testing**
   - Develop AI applications
   - Monitor system resources with JetsonStats
   - Optimize performance and power consumption

5. **Deployment and optimization**
   - Application packaging and system integration
   - Performance tuning and stability testing
   - Industrial environment adaptation and testing

## Quick Start

New users can refer to [Quick Start Guide](../1-Quick%20Start.md) to quickly understand and get started with the NG4500 edge AI box. This guide will help you with the initial setup and guide you through the initial configuration of your system.

## Technical Support and Resource

- [NVIDIA Jetson developer community](https://forums.developer.nvidia.com/c/agx-autonomous-machines/jetson-embedded-systems/70) - NVIDIA® official technical support and forum
- [Jetson Linux API reference](https://docs.nvidia.com/jetson/l4t/) - Jetson Linux reference document for development
- [Jetson Orin dev kit document](https://developer.nvidia.com/embedded/jetson-orin-nano-devkit) - NVIDIA® official dev kit document
- [NVIDIA NGC contents](https://catalog.ngc.nvidia.com/) - NVIDIA® pre-train models and containers
- [Jetson community project](https://github.com/dusty-nv/jetson-inference) - Jetson platform open-source projects and examples

For further technical support, please contact our technical support team.

---

For complete product information please see [NG4500 series product overview](../0-Overview.md).
