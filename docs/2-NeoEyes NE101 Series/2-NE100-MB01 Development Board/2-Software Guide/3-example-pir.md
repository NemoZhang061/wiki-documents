# PIR Sensor

## Overview

This page describes how to use a PIR sensor for intelligent motion detection and automatic snapshots with the NE100-MB01 Vision AI camera, enabling a low-power solution for security and smart home applications.

### PIR Features

**PIR sensor** are commonly used in security and automation systems to detect movement by sensing infrared (heat) radiation emitted by objects. Key features include:

- **Detection Distance**：3–7 meters (depending on the specific model)
- **Detection Angle**：Horizontal 110° × Vertical 90° wide coverage
- **Power Supply**： Operates over a wide voltage range of 3.3V–5V
- **Low Power Consumption**：Ultra-low standby current in the microampere (μA) range makes them highly energy-efficient.

## Preparation

### Hardware

- NE100-MB01 Dev Board
- PIR Sensor

### Software 

#### 1. Firmware

- Download pre-compiled firmware for use：[lowpower_camera/bin/NE_101_PIR.zip](https://github.com/camthink-ai/lowpower_camera/tree/main/bin)

#### 2. Environment Requirements

- **IDE Software**：Visual Studio Code（v1.99.2+）
- **Development Framework**：ESP-IDF Extension（v5.1.6）
- **Example Repository**： 
  [lowpower_camera](https://github.com/camthink-ai/lowpower_camera.git)

## Getting Start

### Using Precompiled Firmware

#### 1. Hardware Connection

1. Connect the PIR sensor to the development board
2. Ensure stable power supply

> For More details please refer to
>  [the Hardware Connection Guide](.././Hardware%20Guide/Hardware%20Connection)

#### 2. Firmware flashing

Refer to the below to flash the firmware：
[the System Flashing and Initialization Guide](./../Software%20Guide/System%20Flashing%20and%20Initialization)

#### 3. PIR Function Verification

1. Power on the device and complete initialization
2. Enter low-power standby mode
3. Trigger the PIR sensor：
   - Observe the status indicator LED response
   - Verify automatic snapshot and upload functionality

> Refer to the complete testing procedure in：
> [Quick Start Guide](./../Quick%20Start)

### Using Source Code Development

#### 1. Clone the repository using the following command

```bash
git clone https://github.com/camthink-ai/lowpower_camera.git
```

#### 2. Project setup

Open the directory in VS Code：

![Project Root Directory](/img/NE101_code_dir.png)

#### 3. Configuration

1. **GPIO Setting**：
   - Use RTC GPIO to support wake-up PIR functionality
   - Avoid interference from external pull-up resistors
   
   A GPIO configuration example is shown below

![GPIO Setting](/img/NE101_example_6.png)

2. **Sensitivity Adjustment**：
   - Adjust detection parameters according to the application scenario

![Sensitivity ](/img/NE101_example_5.png)

#### 4. Compile and deploy the source code

1. Select esp32s3 as the target chip：

![Esp32s3 selection](/img/NE101_idf_IC.png)

2. Select the build button to compile the source code：

![Showing build output](/img/NE101_idf_build.png)

3. Select the flash button to upload the generated firmware to the device：

![screenshot showing flashing process](/img/NE101_idf_flash.png)

#### 5. PIR Function Verification

Same with using precompiled firmware

## Suggestions

### Anti-Interference

- Increase ` PULSE_C` Value（ 2–3 seconds）
- Keep away from motors or inverters

### Environment

- Install at 1.5–2 meters height
- Avoid direct sunlight on the sensor
- Clean the sensor lens regularly
- Adjust detection angle for the scene

> **Debug Tips:**：
> 
> 1. Use a logic analyzer to check GPIO signals
> 2. Check serial logs to find false trigger reasons