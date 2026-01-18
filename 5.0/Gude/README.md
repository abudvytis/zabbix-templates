# Template GUDE Expert Sensor Box 7214 for Zabbix 5.0

This is a Zabbix template for monitoring **GUDE Expert Sensor Box 7214 series** devices via **SNMP**.  
It supports **temperature, humidity, dew point, and air pressure sensors**, including both internal and external probes.

---

## Features

- SNMP monitoring of GUDE Expert Sensor Box 7214
- Automatic discovery of all connected sensors (internal and external)
- Monitoring of:
  - Temperature (°C)
  - Humidity (%)
  - Dew Point (°C)
  - Air Pressure (hPa)
- Trigger prototypes for high/low values
- Graph prototypes for each sensor
- Preprocessing for MAC address formatting
- Compatible with **Zabbix 5.0** (tested) and scalable for future Zabbix versions

---

## Requirements

- Zabbix server **5.0** or later (for this XML version)  
- SNMPv2c access to the device
- GUDE Expert Sensor Box 7214 series firmware supporting standard MIBs  

---

## Installation

1. Download the XML template file.
2. Log in to Zabbix web interface.
3. Go to **Configuration → Templates → Import**.
4. Choose the XML file and click **Import**.
5. Add the template to the desired host.
6. Make sure the host SNMP interface is configured correctly.

---

## SNMP Configuration

- Community string: as configured on your device (default `public` in examples)
- SNMP version: v2c
- OIDs used for discovery and monitoring:
  - Temperature: `1.3.6.1.4.1.28507.67.1.6.1.1.2`
  - Humidity: `1.3.6.1.4.1.28507.67.1.6.1.1.3`
  - Dew Point: `1.3.6.1.4.1.28507.67.1.6.1.1.6`
  - Air Pressure: `1.3.6.1.4.1.28507.67.1.6.1.1.5`
  - Device hostname: `1.3.6.1.2.1.1.5.0`
  - Device model: `1.3.6.1.2.1.1.1.0`
  - MAC address: `1.3.6.1.2.1.2.2.1.6.1`

> **Note:** Discovery will automatically detect internal and external sensors. Only active probes are monitored.

---

## Usage

- **Items:** Data from each sensor is available under:
  - Temperature → *Temperature* application
  - Humidity → *Humidity* application
  - Dew Point / Air Pressure → *Other* application
- **Triggers:** 
  - Alerts for high/low temperature and humidity using template macros:
    - `{$TEMP.HIGH}` / `{$TEMP.LOW}`
    - `{$HUM.HIGH}` / `{$HUM.LOW}`
- **Graphs:** Auto-generated per sensor, with separate colors for each metric.

---

## Notes / Known Limitations

- Zabbix 5.0 automatically scales air pressure units; it may display `1.01KhPa` instead of `1014 hPa`. This will display correctly in later versions (5.2+).
- Preprocessing for MAC address is included and tested; SNMP output must be standard (e.g., `0:19:32:2:4e:50`).
- The template is **XML for Zabbix 5.0**; upgrading to newer Zabbix versions may require conversion to **JSON**.

---

## License

This template is open-source and free to use under the GNU General Public License v3.0.

---

## Author

- Created by [Andrius Budvytis]  
- Tested on Zabbix 5.0 with GUDE Expert Sensor Box 7214 series

---

## Contribution

Feel free to open issues or submit pull requests for:

- Additional triggers
- Improved graphs
- Compatibility with newer Zabbix versions
- Support for other GUDE devices

---

