import AccessoriesTable from '@site/src/components/AccessoriesTable';
import useBaseUrl from '@docusaurus/useBaseUrl';

# WiFi Module

**Fn-Link FG6222MPUC-02 Technical Documentation**

---

### 1. Key Features
| Parameter      | Description                                                  |
| ------------ | ------------------------------------------------------ |
| **Wireless** | Wi-Fi 5 (802.11a/b/g/n/ac) + Bluetooth 5.0             |
| **Interface** | M.2 Key E（PCIe x1 + USB 2.0）                         |
| **Frequency** | 2.4GHz（20/40MHz） + 5GHz（20/40/80MHz）               |
| **MIMO** | 2T2R (2x2 MIMO), MU-MIMO supported                       |
| **Data Rate** | Wi-Fi: up to 866.7 Mbps (5GHz 80MHz), Bluetooth: up to 3 Mbps (EDR) |
| **Operating Temperature** | 0°C to 70°C                                           |
| **Dimensions** | 22mm × 30mm × 2.2mm，（compliant with M.2 2230 standard）              |
| **OS** | Android/Linux/Win CE/iOS/XP/WIN7/WIN10        |

---

### 2. Specifications
#### **RF Performance (Typical Values)**
| Band       | Modulation     | TX Power（dBm） | RX Sensitivity（dBm） |
| ---------- | ------------ | --------------- | ----------------- |
| **2.4GHz** | 802.11b      | 20              | -92（1Mbps）      |
|            | 802.11g/n    | 17              | -70（MCS7）       |
| **5GHz**   | 802.11a/n/ac | 15              | -56（MCS9）       |

#### **Bluetooth**
| Parameter          | Value                    |
| -------------- | ----------------------- |
| **Version**       | Bluetooth 5.0           |
| **Modulation Scheme**   | GFSK/π/4-DQPSK/8DPSK    |
| **Output Power**   | Class 1/2/3（up to 5dBm） |
| **RX Sensitivity** | -70dBm（1Mbps）         |

---

### 3. Product Variants Comparison
| Model             | Interface | Dimensions（mm） | Antenna            | Typical Use Case      |
| ----------------- | --------- | ---------- | -------------- | ------------------ |
| **FG6222MPUC-02** | M.2 Key E | 22×30×2.2  | Dual Antenna (IPEX) | Laptops / Tablets / IPCs |

---

### 4. Installation Guide
#### **Hardware**
1. **Interface Compatibility**  
   - Only supports M.2 Key E slot (commonly found in ultrabooks or industrial PCs).  
   - Ensure the motherboard supports both PCIe x1 (Wi-Fi) and USB 2.0 (Bluetooth) signals.  
2. **Antenna**  
   - Use dual-band antennas (2.4GHz/5GHz) and connect them securely via IPEX connectors.  
   - Avoid contact between the antenna and metal components to prevent signal degradation.

<div style={{ display: 'grid', gridTemplateColumns: '1fr', gap: '20px', justifyContent: 'center', alignItems: 'center' }}>
  <img src={useBaseUrl('/img/Hardware_Dev_Resources/WiFi_Module/WiFi_Module.jpg')} alt="WiFi_Module" style={{ height: '400px', objectFit: 'contain', margin: '0 auto' }} />
</div>
