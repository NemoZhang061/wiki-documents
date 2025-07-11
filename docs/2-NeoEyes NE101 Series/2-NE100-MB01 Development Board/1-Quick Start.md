# Quick Start

## Product Overview

The NeoEyes NE100 series is a high-performance smart camera product line specially designed for IoT (Internet of Things) applications. The NE101 event-triggered camera provides key functions such as scheduled image capture and data reporting. This guide will help you master the product quickly.

## Hardware Preparation

### Hardware Components

- NE100-MB01 development kit
- Specific module board (optional), please refer to [Hardware Component Overview](./Hardware%20Guide/Components%20Overview)

## Operation Guide

### Device Connection

![NE101 main board1](/img/NE101_Main_Board.png)  
![NE101 main board2](/img/NE101_Main_Board2.png)  

**Notes**：

1. Powered by Type-C interface (5V/1A or above)
2. The interface adopts fool-proof design
3. Reserve debugging serial port (115200bps)

For detailed hardware connections, please refer to: [Hardware Connection Guide](./Hardware%20Guide/Hardware%20Connection)

### Quick Start Process

1. **Power on the device**
   
   - Connect USB power

2. **Confirm the status**
   
   - The power indicator light lights up for 1 second to indicate successful startup.
   - System initialization takes about 1 minute.

3. **Enter configuration mode**
   
   - Press and hold the function button, wait until the light turns on and then release it (about 3-4 seconds).

4. **Connect to management interface**
   
   - The device hotspot name is displayed as NE101_XXXXXX
   - Use mobile phone/computer to connect the device Wi-Fi
   - Visit http://192.168.1.1

![wifi connect](/img/NE101_wifi_connect.png)
![web interface](/img/NE101_web.png)

### Core Function Configuration

#### Image Collection Setup

![real-time web](/img/NE101_web_cam.png)

**Key Parameters**：

- **Flash Mode**：
  
  - Auto (default)
  - Scheduled on
  - Force shut down

- **Image Adjustment**：
  
  - Brightness level adjustment: 0-90.
  - Image adjustment: brightness/contrast/saturation (this option is not available when using USB module).
  - Screen mirroring function (this option is not available when using USB module).

![imageadjustment](/img/NE101_web_ImageAdjustment.png)

#### Scheduled Image Capturing Configuration

![cap setting](/img/NE101_web_cap_setting.png)

**Operation Mode**：

1. **Timer Shooting**: Set a specific time point
2. **Interval Shooting**: Set the cycle period (5 minutes-24 hours)
3. **External trigger mode**: Triggered by PIR
4. **Manual Mode**: Press the button to trigger shooting

#### Network Connection and Data Reporting

![network connection](/img/NE101_web_WLANConnection.png)

**Network test (serial port connection)**：

```bash
# Example of ping test through serial port
ping www.example.com -c 4
```

![network testing](/img/NE101_ping.png)

**Data Reporting**：

1. Configure MQTT server parameters
2. Use MQTTX tool to verify data flow
3. Check the reporting status

![datareport](/img/NE101_web_DataReport.png)
![MQTT data](/img/NE101_MQTT.png)

**MQTTX User Manual：**

1. Open MQTTX, and click `Set up new connection`.

2. Configure connection parameters：
   
   - **Host**：Server address`xxx.xxx.xxx.xxx`
   - **Port**：Server port`xxx`
   - **Client ID**：Any letter, for example `mqttx-client-01`
   - **Topic**：For example `camera1`
   - **Username / Password**：Set up according to the server

3. Click connect, then subscribe Topic `camera1`。

**Data Format Description：**

The MQTT message payload content sent by the device is in JSON format, as shown below:

```json
{
  "ts": 1740640441620,
  "values": {
    "devName": "NE101 Sensing Camera",
    "devMac": "D8:3B:DA:4D:10:2C",
    "battery": 84,
    "snapType": "Button",
    "localtime": "2025-02-27 15:14:01",
    "imageSize": 74371,
    "image": "data:image/jpeg;base64,..."
  }
}
```

**Field description：**

- `ts`：timestamp (milliseconds)
- `devName`：device name
- `devMac`：device MAC address
- `battery`：battery level (percentage)
- `snapType`：image capture type（for example `Button`, `Timer`, `Alarm in`, etc.）
- `localtime`：local time (string format)
- `imageSize`：image size (unit: bytes)
- `image`：Base64 encoded JPEG image data, prefixed by`data:image/jpeg;base64,`

**Visualization Suggestion：**

Use Base64 image data to quickly preview images on web pages or tools:

```html
<img src="data:image/jpeg;base64,...">
```

Or paste Base64 data into [Base64 Image Viewer](https://base64.guru/converter/decode/image) for online preview.

### Functional Verification Process

1. Enter sleep mode (wait for 5 minutes to wake up automatically).
2. Trigger shooting tasks (timer/manual/external trigger).
3. Confirm image quality (resolution/exposure/focus).
4. Verify data upload (server receives confirmation to confirm whether the received image is normal).

![cap success](/img/NE101_cap_success.png)

## Detailed Explanation of Device Working Mode

| Mode  | Trigger Condition | Duration  | Key Features     |
| --- | ---- | ----- | --------- |
| Initialization | Power on automatically | about 1 minute  | System self-test, time synchronization |
| Configuration  | Press button | 1-5 minute | Configure parameters, monitor status |
| Operation  | By pre-set schedule | Calculated by actual practice  | Image capture, data reporting |
| Sleep mode  | Automatic | By schedule  | Low power consumption standby     |

## Premium Functions

### Device Maintenance

- **Hardware Reset**: Press the reset button shortly to reset.
- **Hardware Reset**：Press the function key for 10-11s to reset all configuration.
- **Device Information**：View the MAC address/firmware version on the management interface.
- **Wireless Upgrade**：Supports OTA firmware update on the management interface.

![OTA upgrade](/img/NE101_ota.png)

> **Technical Support**: It is recommended to complete a full functional test for first time use.
