# Development Environment Setup

## Overview

This guide provides a complete walkthrough for setting up the ESP32-S3 development environment on Windows, based on Espressif’s official ESP-IDF v5.1.6 framework. It offers two mainstream development options: using the VS Code extension (recommended) or configuring the command-line toolchain. We strongly recommend using Visual Studio Code for an optimal development experience.

Official Reference：[Programming Guide](https://docs.espressif.com/projects/esp-idf/en/release-v5.1/esp32s3/get-started/index.html)

## Development Tools Options

Two installation methods are available for setting up the IDE tools：

1. [Eclipse Plugin](https://github.com/espressif/idf-eclipse-plugin/blob/master/README.md)（Suitable for developers already familiar with the Eclipse environment.）
2. [VSCode Extension](https://github.com/espressif/vscode-esp-idf-extension/blob/master/docs/tutorial/install.md)（Recommended for a smoother and more user-friendly development experience.）

## Command-Line Development (Optional)

For advanced users who prefer CLI-based workflows, refer to：[Standard Toolchain Setup for Windows](https://docs.espressif.com/projects/esp-idf/en/release-v5.1/esp32s3/get-started/windows-setup.html)

## Setting Up VS Code (Recommended)

### Setup Steps

1. **Install Visual Studio Code**
   
   - Download and install the latest version from the [VSCodewebsite](https://code.visualstudio.com/).
   - Launch VSCode, search for and install the "Espressif IDF" extension from the extension marketplace.
   
   ![VSCode extension](/img/NE101_Setup_idf1.png)

2. **Configure the ESP-IDF Development Environment**
   
   - Press `Ctrl+Shift+P` to open the command palette.
   - Type and select the command `Configure ESP-IDF extension`.
   
   ![command palette](/img/NE101_Setup_idf2.png)

### Installation Modes

Three installation modes are available to suit different setup preferences：

![Installation Modes ](/img/NE101_Setup_idf3.png)

1. **EXPRESS**（Recommended）
   
   - Automatically downloads and installs the specified ESP-IDF version (recommended: v5.1.6)
   - Automatically creates a Python virtual environment
   - Default installation path：`X:\Espressif`
   - Note: This method relies on GitHub for downloading components. Users in mainland China may need to configure a proxy.

2. **ADVANCED**
   
   - Allows custom selection of ESP-IDF version and Python environment
   - Supports managing multiple ESP-IDF versions
   - Allows setting a custom toolchain installation directory

3. **USE EXISTING SETUP**
   
   - Detects an existing ESP-IDF environment on your system
   - Recommended for users who have already configured the development environment

It is recommended to choose the **EXPRESS** and and start with version v5.1.6.

![selecting](/img/NE101_Setup_idf4.png)
![setup process](/img/NE101_Setup_idf5.png)

The following screen will be displayed upon successful installation:

![successful installation](/img/NE101_Setup_idf6.png)

## Project Development

### Get the Project Code

Clone the project repository using Git：

```bash
git clone https://github.com/camthink-ai/lowpower_camera.git
```

### Flash the Firmware

1. **Open the Project**
   
   - In Visual Studio Code, go to File > Open Folder.
   - Navigate to the folder where the project is located.
   
   ![项目目录结构](/img/NE101_CodeList.png)
   ![项目文件浏览](/img/NE101_CodeList1.png)

2. **Project setup**
   
   - Select the correct COM port from the bottom status bar.
   - Select esp32s3 as the target chip.
   
   ![target chip](/img/NE101_idf_IC.png)

3. **Compile and deploy the source code**
   
   - (Optional) Run the"menuconfig"command to modify project configuration.
   - Select the build button to compile the source code：
   
   ![Compile process](/img/NE101_idf_build.png)
   
   - Select the flash button to upload the generated firmware to the device：
   
   ![Showing build output](/img/NE101_idf_flash.png)

## Environment Verification

After flashing is complete, the device will reboot automatically. You can use the integrated Serial Monitor in Visual Studio Code to view the startup logs and verify that the firmware is running correctly.

> Important Notes：
> 1. For first-time users, it's recommended to run an official example to verify the environment setup.
> 2. If you experience network issues during component downloads, consider configuring a local mirror for faster access.
> 3. During development, ensure a stable USB connection to avoid flashing interruptions.

This guide covers the essential steps for setting up the ESP32-S3 development environment. For advanced configuration options, please refer to the official Espressif documentation or contact technical support.
