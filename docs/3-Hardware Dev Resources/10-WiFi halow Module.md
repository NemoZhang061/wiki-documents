import AccessoriesTable from '@site/src/components/AccessoriesTable';
import useBaseUrl from '@docusaurus/useBaseUrl';

# Wi-Fi HaLow Module

## Module Key Features
### Description
FGH100M is a long-distance, low-power Wi-Fi HaLow module that is compliant with the IEEE 802.11ah protocol. It supports the Sub-1 GHz frequency band and is suitable for IoT and smart device scenarios. Applicable to CamThink NeoEyes NE101 series motherboards.

### Key Features

| 1    | Items                  | Description            |
| ---- | ------------------------ | -------------------------- |
| 2    | WiFi Protocol            | IEEE 802.11 ah             |
| 3    | Operating Modes          | AP/STA                     |
| 4    | Operation Frequencey     | Sub-1 G: 850–950 MHz       |
| 5    | Channel Width            | 1 MHz, 2 MHz, 4 MHz, 8 MHz |
| 7    | Antenna                  | PCB Antenna                |
| 8    | Communication Interfaces | SPI                        |
| 9    | Power Supply             | DC 4-6V                    |
| 10   | Operation Temperature    | -20℃ ~ +60℃                |
| 11   | Storage Temperature      | -40℃ ~ +85℃                |
| 12   | Dimensions               | 60 x 60 mm                 |
| 12   | Certifications           | CE/FCC                     |

## Interfaces Introduction (J1)

The module communicates with the motherboard through SPI by J1 interface. The interface is defined as follows:

| PIN# | Pin Name  | Functions          | Pin Type | Pull Up/Down |
| ---- | --------- | ------------------ | -------- | ------------ |
| 1    | WIFI_BUSY | SDIO Clock Signal  | GPIO     | N/A          |
| 2    | WIFI_RST  | Reset Module       | IN       | Pull-Up      |
| 3    | WIFI_PWR  | High=ON;Low=OFF    | IN       | N/A          |
| 4    | WIFI_WAKE | Wake up Module     | IN       | N/A          |
| 5    | SPI_CS    | SPI_CS             | SPI      | Pull-Up      |
| 6    | INT       | INT                | GPIO     | Pull-Up      |
| 7    | NC        |                    |          |              |
| 8    | SPI_MISO  | SPI_MISO           | SPI      | Pull-Up      |
| 9    | GND       | GND                | POWER    |              |
| 10   | GND       | GND                | POWER    |              |
| 11   | SPI_CLK   | SPI Clock          | SPI      | Pull-Up      |
| 12   | SPI_MOSI  | SPI_MOSI           | SPI      | Pull-Up      |
| 13   | NC        |                    |          |              |
| 14   | 3V3       | 3.3 V power supply | POWER    |              |
| 15   | NC        |                    |          |              |
| 16   | 3V3       | 3.3 V power supply | POWER    |              |

## Dimensions

60x60 mm
60*60mm
<div style={{ display: 'grid', gridTemplateColumns: '1fr', gap: '20px', justifyContent: 'center', alignItems: 'center' }}>
  <img src={useBaseUrl('/img/Hardware_Dev_Resources/WiFi_Halow/wifihalow.jpg')} alt="wifihalow" style={{ height: '400px', objectFit: 'contain', margin: '0 auto' }} />
</div>
