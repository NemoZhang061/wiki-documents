# Human Face Detection

## Overview

This example demonstrates human face detection based on deep learning and provides a lightweight, extensible framework for face-related applications.

The project is developed using the[ESP-DL](https://github.com/espressif/esp-dl) library,which offers deep learning capabilities within the ESP-WHO framework. With support for different hardware modules, it can be used in various AIoT scenarios.

## Development Preparation

### Hardware

- NE100-MB01 Development Board

### Software

#### 1. Firmware：

Download pre-compiled firmware for use：

- [human_face_detect.zip](https://github.com/camthink-ai/esp-who/blob/master/bin)

#### 2. Environment Requirements

To perform secondary development, make sure the following：

- **IDE Software**：Visual Studio Code（v1.99.2+）
- **Development Framework**：ESP-IDF Extension（v5.1.6）
- **Example Repository**：[camthink-ai/esp-who](https://github.com/camthink-ai/esp-who)

> **Important**：Please follow the [Development Environment Setup Guide](./../NE100-MB01%20Development%20Board/Software%20Guide/Development%20Environment%20Setup) to complete the initial configuration.

## Functionality Verification

### Using Precompiled Firmware

#### 1. Hardware Connection

Connect the development board to PC using a Type-C cable.

![NE101 interface](/img/NE101_Main_Board2.png)

#### 2. Firmware flashing

Refer to the detailed flashing guide：

- [System Flashing and Initialization](./../NE100-MB01%20Development%20Board/Software%20Guide/System%20Flashing%20and%20Initialization)

#### 3. UART Output Analysis

The device outputs face detection results via the serial port (baud rate: 115200)：

Example Code:

```
WhoDetect: 0, bbox: [0.826712, 47, 40, 169, 195], left_eye: [80, 105], left_mouth: [90, 151], nose: [101, 125], right_eye: [123, 99], right_mouth: [126, 146]
```

**Field Descriptions**：

- **bbox**：Face bounding box information
  - Format：[confidence, top-left x, top-left y, width, height]
- **left_eye**：Coordinates of the left eye(x,y)
- **right_eye**： Coordinates of the right eye (x,y) 
- **nose**：Coordinates of the nose(x,y)
- **left_mouth**：Coordinates of the left mouth corner(x,y)
- **right_mouth**：Coordinates of the right mouth corner(x,y)

#### 4. Performance Test

1. Point the camera at a real human face or a face image.
2. Observe the serial output for facial landmark data.
3. Move the camera around to test dynamic face detection performance.

![Static Illustration of Face Detection](/img/NE101_example_human_detect_1.png)

![Real-Time Face Detection Example](/img/NE101_example_human_detect.gif)

### Source Code Development

#### 1. Clone the repository using the following command

```bash
git clone https://github.com/camthink-ai/esp-who
```

#### 2. Project setup

1. Open the directory in VS Code：`examples/human_face_detect`
   
   ![Project Root Directory](/img/NE101_human_face_detect_dir.png)

2. Select esp32-s3 as the target chip：
   
   ![芯片选择界面](/img/NE101_idf_IC.png)

#### 3. Compile and deploy the source code

1. Select the build button to compile the source code：
   
   ![Esp32s3 selection](/img/NE101_idf_build.png)

2. Select the flash button to upload the generated firmware to the device：
   
   ![Showing build output](/img/NE101_idf_flash.png)

#### 4. Performance Test

Same with using precompiled firmware

## References

1. ESP-DL Model Quantization Documentation：
   
   - [GitHub - espressif/esp-dl](https://github.com/espressif/esp-dl?tab=readme-ov-file)

2. Official Example Repository：
   
   - [GitHub - espressif/esp-who](https://github.com/espressif/esp-who/tree/master)
