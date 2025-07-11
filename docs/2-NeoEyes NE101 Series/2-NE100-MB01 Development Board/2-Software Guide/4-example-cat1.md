# Low-Power Image Capture Base on Cellular (LTE Cat 1)

## Overview

This guide describes how to achieve low-power image capture and transmission in outdoor environments using LTE Cat 1 technology. It is particularly suitable for scenarios without Wi-Fi coverage or gateway devices.

### Key Features

**LTE Cat 1** is a 3GPP standard designed for IoT, offers the following key advantages:

- **Efficient Data Transmission**：Supports up to 10 Mbps downlink and 5 Mbps uplink
- **Full Feature Support**：including VoLTE and mobility, making it suitable for various IoT and M2M applications
- **Power Efficiency**：Optimized for battery-powered, long-term deployments
- **Global Coverage**：Leverages existing 4G LTE networks, providing widespread coverage in many regions. 

## Preparation

### Hardware

- NE100-MB01 Development Board
- LTE Cat 1 Module
- Activated 4G SIM Card

![Cat1Module](/img/Overview/NE101/cat1PCBA.png)

### Software

#### 1. Firmware

- Download pre-compiled firmware for use：[lowpower_camera/bin/NE_101_FCC.zip](https://github.com/camthink-ai/lowpower_camera/tree/main/bin)

#### 2. Environment Requirements

- **IDE Software**：Visual Studio Code（v1.99.2+）
- **Development Framework**：ESP-IDF Extension（v5.1.6）
- **Example Repository**： 
  [lowpower_camera](https://github.com/camthink-ai/lowpower_camera.git)

## Functionality Verification

### Using Precompiled Firmware

#### 1. Hardware Setup

1. Ensure the Cat 1 module is properly installed.
2. Insert an activated 4G SIM card.

> For More details please refer to [the Hardware Connection Guide](.././Hardware%20Guide/Hardware%20Connection)

#### 2. **Firmware flashing**：

   Refer to the below to flash the firmware：
   
    [the System Flashing and Initialization Guide](./../Software%20Guide/System%20Flashing%20and%20Initialization)

#### 3. Verify Network Status

1. Long-press the function button to enter Network configuration mode
2. Access the Web UI at http://192.168.1.1
3. Check the “Cellular Network” status panel

![status panel1](/img/NE101_example_cat1_1.png)
![status panel2](/img/NE101_example_cat1_2.png)

#### 4. Data Transmission Test

1. Configure MQTT server parameters
2. Test image capture and upload functionality

> Refer to the complete testing procedure in：
> [Quick Start Guide](./../Quick%20Start)

### Developing from Source

#### 1. Clone the repository using the following command

```bash
git clone https://github.com/camthink-ai/lowpower_camera.git
```

#### 2. Project setup

Open the directory in VS Code：

![Project Root Directory](/img/NE101_code_dir.png)

#### 3. Compilation and Deployment

1. Select the build button to compile the source code：

![Showing build output](/img/NE101_idf_build.png)

2. Select the flash button to upload the generated firmware to the device：

![screenshot showing flashing firmware](/img/NE101_idf_flash.png)

#### 4. Verify Network and Data Transmission

Same with using precompiled firmware

## Notes

### SIM Card Management

- Ensure the SIM card has active 4G data service

### Signal Quality Guidelines

- **Good**：RSSI > -85dBm
- **Fair**：-85dBm > RSSI > -95dBm  
- **Weak**：RSSI < -95dBm

> **Development Tips**：
> 
> 1. Use a serial tool to monitor AT command responses for troubleshooting
> 2. Network registration may take 30–60 seconds, which is normal
> 3. In low-signal environments, try repositioning the device for better coverage

