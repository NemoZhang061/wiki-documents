
import AccessoriesTable from '@site/src/components/AccessoriesTable';
import useBaseUrl from '@docusaurus/useBaseUrl';

#### **Product Features**   
This product is a high-performance USB camera module equipped with a 1/2.7-inch 2MP image sensor, capable of delivering 1080P 30fps HD video output.

**Key Specifications**  
| No.| Items                    | Description       |        Remarks       |
| ---- | ------------------------ | ----------------- | ------------- |
| 1    | CMOS Sensor              | SC200AI, 1/2.8"   |               |
| 2    | Max.Resolution           | 1920*1080         |               |
| 3    | F.No                     |                   | Optional LENS |
| 4    | Focal Length             | 2.5mm/4mm/6mm     | Optional LENS |
| 5    | Focusing distance        | 2M/3M/5M          | Optional LENS |
| 6    | FOV(H)                   | 137/88/51         | Optional LENS |
| 8    | Communication Interfaces | USB               |               |
| 9    | Operation Temperature    | -20°-- 60°        |               |
| 10   | Storage Temperature      | -40°-- 85°        |               |
| 11   | Dimensions               | 25mm*23.86mm      |               |

---

#### **Pin Definition (4-pin USB Interface)**  
| **Pin** | **v** | **Function**    | **Remarks**         |
| ----------- | ------------ | --------------- | ---------------- |
| 1           | VCC          | 5V Power Input      | Max current 500mA    |
| 2           | DM           | USB D- Signal | Compliant with USB 2.0 protocol |
| 3           | DP           | USB D+ Signal | Compliant with USB 2.0 protocol |
| 4           | GND          | Ground          | Shared with signal ground     |

---

#### **Usage**  
1. **Hardware Connection**  
   - Connect to the host via the 4-pin 1.0mm USB interface, Ensure stable power supply during operation.   
   - The lens is pre-focused at the factory; do not rotate or disassemble the lens module.  

2. **System Compatibility**  
   - Supported OS: Windows XP / 7 / 8.1 / 10, macOS, and Linux 2.6.2 or above (requires built-in UVC driver).  
   - Minimum system requirements：CPU ≥ 1.7GHz, Memory ≥ 512MB, HDD ≥ 40GB, OS: XP SP2 or later.  

3. **Notes**  
   - Operating temperature should be maintained between 0°C and 60°C. Avoid environments with condensation.  
   - Use a lint-free cloth to clean the lens. Do not use corrosive solvents.  

---

#### **4. Dimension **  
<div style={{ display: 'grid', gridTemplateColumns: '1fr', gap: '20px', justifyContent: 'center', alignItems: 'center' }}>
  <img src={useBaseUrl('/img/Hardware_Dev_Resources/USB_Module/USB_Module_Size.png')} alt="USB_Module_Size" style={{ height: '400px', objectFit: 'contain', margin: '0 auto' }} />
</div>
