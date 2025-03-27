# Water Tank Level Sensor

A smart water level monitoring system for underground rainwater tanks using ESPHome on an ESP32-C6 microcontroller. This project measures water level, temperature, and humidity, and sends the data to a cloud dashboard.

## Overview

This system monitors:
- Water level and volume in an underground rainwater tank (e.g. Graf Regenwassertank/Zisterne)
- Temperature and humidity
- Battery voltage
- WiFi signal strength

![Water Tank](images/water-tank.jpg "Water-Tank")  
image of board, dashboard, datacake dashboard

## Requirements

### Hardware 

- ESP32 programmable chip e.g. Seeed XIAO ESP32-C6 8MB https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html 
- Ultrasonic distance sensor e.g. JSN-RS04t or AJ-SR04M
- Temperature & humidity sensor e.g. AM2302 

### Software 

- Python 
- PlatformIO https://platformio.org/
- Espressif https://www.espressif.com/en/products/socs/esp32
- ESPHome https://esphome.io/

## Installation

1. Clone this repository
2. Copy `/common/secrets-template.yaml` to `/common/secrets.yaml` and configure your WiFi credentials
3. Install ESPHome and dependencies:
   ```bash
   pip install esphome
   ```
4. validate the configuration:
   ```bash  
   esphome config water-tank.yaml
   ```
5. Connect your ESP32-C6 to your computer via USB
6. Flash the firmware:
   ```bash
   esphome run water-tank.yaml
   ```

## Usage

Once installed, the device will:
1. Wake up at configured intervals to take measurements
2. Send data to your configured dashboard (DataCake)
3. Go back to deep sleep to conserve battery power

You can adjust the measurement frequency and other parameters in the `water-tank.yaml` configuration file.

## Wiring

![Breadboard of Water Tank Level](images/breadboard-water-tank-level.png "Breadboard")  
Breadboard wiring of the water tank level

### Pin Configuration

The following pins are used in this project:
```yaml
  pin_battery_voltage: GPIO0  # GPIO0 D0
  pin_wakeup:          GPIO1  # GPIO1 left/bottom (only pins 0, 1, 2, 3, 4, 5, 6, 7 may support wakeup)
  pin_dht:             GPIO2  # GPIO2 D2
  pin_ultrasonic_rx:   GPIO18 # GPIO18 Rx/Trig
  pin_ultrasonic_tx:   GPIO20 # GPIO20 Tx/Echo
```

## Dashboard

The dashboard was realized using [DataCake](https://datacake.co/) which displays the current and past water level, battery level and the temperature and humidity.

![Dashboard](/images/dashboard.png)  
DataCake Dashboard

## Troubleshooting

Common issues:
- **Inaccurate readings**: Make sure the ultrasonic sensor is properly positioned and not obstructed
- **Battery drains quickly**: Check the deep sleep configuration in your YAML file
- **Connection issues**: Verify WiFi credentials and signal strength at the installation location

## Resources

- [Getting Started with Seeed Studio XIAO ESP32C6](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/)
- [ESPHome Documentation](https://esphome.io/)
- [DataCake Documentation](https://docs.datacake.de/)

## Contact

- Autor: Roland Ortner
- Date: 2025-03-27
- LinkedIn: https://www.linkedin.com/in/roland-ortner/
- Reports: battery voltage, WiFi signal, level and volume in water tank
- Icons: https://pictogrammers.com/library/mdi/

## License

This project is open source and available under the [MIT License](LICENSE).

<img src="images/made-for-esphome-white-on-black.png" title="Made for ESPHome" alt="Made for ESPHome Logo" width=150>