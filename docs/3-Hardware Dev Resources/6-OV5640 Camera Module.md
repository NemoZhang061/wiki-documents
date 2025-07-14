import AccessoriesTable from '@site/src/components/AccessoriesTable';
import useBaseUrl from '@docusaurus/useBaseUrl';

# OV5640 Camera Module

## Product Features

### Key Highlights
- **Sensor**：OmniVision OV5640 CMOS sensor (1/4" optical format)
- **Resolution**：2592×1944 pixels (5MP)
- **Optics**： Available in 60° or 120° FOV versions
- **Focusing Distance**：Supports focusing at 8 cm or 3 m

### Model Comparison Table

| Parameter            | OV5640 Module (60°) | OV5640 Module (120°) |
| ---------------- | ------------------- | -------------------- |
| **FOV** | 60°                 | 120°                 |
| **Focal Lengt (mm)**    | 3.97                | 1.79                 |
| **Aperture(F/No)**  | 2.4                 | 2.0                  |
| **Focusing Distance**     | 15cm or 400cm       | 8cm or 300cm         |

---

## Specifications

| Parameter         | Description                    |Remarks                |
| --------------- | -------------------------- | -------------------- |
| **Max Resolution**  | 2592×1944                  |  JPEG/YUV 	Supported    |
| **Optical Format**    | 1/4"                       | OmniBSI™       |
| **Pixel **      | 5MP                      |                      |
| **FOV**         | 60° / 120°                 | Optional versions             |
| **Aperture (F/No)** | 2.4（60°） / 2.0（120°）   | Larger aperture improves low-light performance |
| **Focal Length (mm)**   | 3.97（60°） / 1.79（120°） | Shorter focal length enables ultra-wide FOV  |
| **Focusing Distance**    | 8cm  or  3m                | Supports both close-up and distant scenes  |
| **Operating Temperature**    | -10°C ~ +65°C              | Industrial-grade temperature range      |

---

## Module Pinout

| Pin | Signal  | Type | Description                |
| ------ | -------- | ---- | -------------------------- |
| 1      | NC       | -    | Not Connected                    |
| 2      | AGND     | Ground   | Analog Ground                     |
| 3      | SDA      | I/O  | SCCB Data Line |
| 4      | AVDD     | 	Power | Analog Power (2.8V)           |
| 5      | SCL      | I/O  | SCCB Clock Line           |
| 6      | RESET    | Input | 	Hardware Reset (Active High)     |
| 7      | VSYNC    | Output| Vertical Sync               |
| 8      | PWDN     | Input | Power Down Control (Active High) |
| 9      | HSYNC    | Output |Horizontal Sync                |
| 10     | DVDD     | Power| Digital Core Power （1.5V）       |
| 11     | DOVDD    | Power | Digital Output Power （1.8V）       |
| 12     | D9       | Output | Image Data Bit（D9）         |
| 13     | MCLK     | Input | Master Clock Input （24MHz）        |
| 14     | D8       | Output | Image Data Bit（D8）         |
| 15     | GND      | Ground | Digital Ground                     |
| 16     | D7       | Output | Image Data BitD7）         |
| 17     | PCLK     | Output | Pixel Clock             |
| 18     | D6       | Output | Image Data Bit（D6）         |
| 19     | D2       | Output | Image Data Bit（D2）         |
| 20     | D5       | Output | Image Data Bit（D5）         |
| 21     | D3       | Output | Image Data Bit（D3）         |
| 22     | D4       | Output | Image Data Bit（D4）         |
| 23     | NC       | -    | Not Connected                    |
| 24     | NC       | -    | Not Connected                 |

---

## Usage

### Installation
1. **Hardware Connection**：
   - Connect the FPC connector (38.5×12.5 mm, 24-pin @ 0.5 mm pitch) to the host board.
   - Ensure proper wiring for power (AVDD/DVDD/DOVDD) and ground (AGND/DGND).

2. **Initialization**：
   - Configure the module via the SCCB interface (SDA/SCL) by writing to registers (refer to the `Register Tables` in`OV5640 datasheet` ）
   - Set parameters such as FOV, exposure time, and gain.

3. **Image Output**：
   - Enable the DVP (Digital Video Port) interface，Set the data format to YUV422 or RGB565.
   - Use VSYNC and HREF signals to synchronize and read image frames.

### Notes
- **ESD Protection**：Always wear an anti-static wrist strap during operation.
- **Power Stability**：Ensure AVDD voltage fluctuation is within ±5%.
- **Thermal Considerations**：Adequate heat dissipation is required for prolonged operation.

## Dimension
![NG45_PCBA_IO_Bottom](/img/Hardware_Dev_Resources/OV5640_Module/OV5640_Module_Outline.png)

