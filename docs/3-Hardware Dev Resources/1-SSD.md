import AccessoriesTable from '@site/src/components/AccessoriesTable';
import useBaseUrl from '@docusaurus/useBaseUrl';

## 1. Key Features
| Feature                  | Description                                                     |
| :----------------------- | :-------------------------------------------------------------- |
| **Capacity**             | 256GB / 512GB / 1TB                                             |
| **Form Factor**          | M.2 2280 (22mm × 80mm × 2.3mm, weight ≤9.5g)                    |
| **Interface**            | PCIe Gen3 ×4, NVMe 1.3 protocol                                 |
| **Flash Type**           | 3D TLC NAND (supports ×2/×4 interface)                          |
| **Performance (1TB typical)** | Sequential Read: 3234 MB/s<br>Sequential Write: 3099 MB/s     |
| **Power Consumption (1TB typical)** | Active Write: 2989mW<br>Active Read: 2733mW<br>Idle: 693mW   |
| **Operating Temperature**| 0°C to 70°C (Storage: -40°C to 85°C)                            |
| **Reliability**          | MTBF > 2M hours<br>Supports SMART monitoring, dynamic/static wear leveling, RAID engine protection |
| **Advanced Features**    | NANDXtend ECC correction, Over-Provisioning                    |

---

## 2. Specifications
### Basic Specifications
| Parameter             | Specification                                                  |
| :-------------------- | :------------------------------------------------------------- |
| **Interface Speed**   | PCIe 3.0 ×4 (8Gb/s per lane)                                   |
| **Supported Command Set** | NVMe 1.3 standard commands<br>Power management (ASPM/APST)<br>SMART health information |
| **Endurance (TBW)**   | 256GB: 160TB<br>512GB: 320TB<br>1TB: 640TB                     |
| **Humidity**          | 90% RH (40°C non-condensing)                                   |

### Electrical Specifications
| Parameter          | Specification                                                  |
| :----------------- | :------------------------------------------------------------- |
| **Supply Voltage** | 3.3V ±5%                                                       |
| **Pin Definition** | Standard PCIe pins<br>Includes 4 differential signal channels<br>Supports L0/L1 low-power states |

---



## 3. Series Model Comparison

### Performance Comparison (Typical Values)
| Model             | Seq. Read (MB/s) | Seq. Write (MB/s) | Rand. Read (K IOPS) | Rand. Write (K IOPS) | Power (Active Read) | Power (Active Write) |
| :---------------- | :--------------- | :---------------- | :------------------ | :------------------- | :------------------ | :------------------- |
| **NS256GSSD530**  | 3190             | 3061              | 135                 | 64                   | 2041mW              | 1423mW               |
| **NS512GSSD530**  | 3228             | 3090              | 134                 | 75                   | 2921mW              | 1598mW               |
| **NS1T0BSSD530**  | 3234             | 3099              | 132                 | 92                   | 2733mW              | 2989mW               |

### Test Conditions
- **Hardware Platform**: Intel i9-9900X + 32GB DDR4 + X299 chipset  
- **Software Environment**: Windows 10 x64<br>CrystalDiskMark 8.0 / AS SSD 2.0 / IOMeter  
- **Note**: Performance may vary based on system configuration, firmware version, or temperature fluctuations.

---

## 4. Usage Instructions
### Installation & Compatibility (*Pending installation images and system commands/images*)
1. **Physical Installation**:  
   - Power off device, insert SSD into M.2 2280 slot, secure with screw  
2. **System Configuration**:  
   - Enable AHCI mode and NVMe drivers，disable power-saving modes in power management for optimal performance  

### Precautions
- **Temperature Control**: Avoid prolonged high-load operation (>70°C), improve chassis cooling  
- **Data Security**: Regularly back up critical data to prevent corruption from sudden power loss  
- **ESD Protection**: Wear anti-static gloves during installation to prevent component damage  

---

<div style={{ display: 'grid', gridTemplateColumns: '1fr', gap: '20px', justifyContent: 'center', alignItems: 'center' }}>
  <img src={useBaseUrl('/img/Hardware_Dev_Resources/SSD/SSD_TopView.jpg')} alt="SSD_TopView" style={{ height: '400px', objectFit: 'contain', margin: '0 auto' }} />
</div>
