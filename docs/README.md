# Water Tank Level Sensor - Detailed Documentation

This document provides detailed information about the water tank level monitoring system, including all hardware components, setup instructions, and visual documentation.

## Table of Contents
- [System Overview](#system-overview)
- [Hardware Components](#hardware-components)
- [Wiring and Assembly](#wiring-and-assembly)
- [Enclosure and Installation](#enclosure-and-installation)
- [Dashboard and Visualization](#dashboard-and-visualization)
- [Technical Specifications](#technical-specifications)

## System Overview

The water tank level monitoring system is designed to measure and report the water level in underground rainwater tanks. It uses an ESP32-C6 microcontroller with ESPHome firmware to collect data from various sensors and transmit it to a cloud dashboard.

![Water Tank Overview](/docs/images/water-tank-overview.png)
*Complete overview of the water tank monitoring system*

![Water Tank Sensor](/docs/images/water-tank-sensor.png)
*Close-up of the water tank level sensor*

## Hardware Components

### Main Components

- **ESP32-C6 Board**: Seeed XIAO ESP32-C6 with 8MB flash memory
- **Ultrasonic Sensor**: JSN-RS04t or AJ-SR04M waterproof ultrasonic distance sensor
- **Temperature & Humidity**: AM2302/DHT22 sensor
- **Power Supply**: 3.7V LiPo battery with JST connector

### Water Tank

![Water Tank](/docs/images/water-tank.png)
*The water tank with the monitoring system installed*

## Wiring and Assembly

### Breadboard Layout

The following image shows the breadboard layout for connecting all components:

![Breadboard of Water Tank Level](/docs/images/breadboard-water-tank-level.png)
*Breadboard wiring diagram showing all connections between the ESP32-C6, ultrasonic sensor, and DHT22*

### Pin Configuration

```yaml
pin_battery_voltage: GPIO0  # GPIO0  D0  - Voltage ADC
pin_wakeup:          GPIO1  # GPIO1  D1  - Wakeup (only pins 0, 1, 2, 3, 4, 5, 6, 7 may support wakeup)
pin_dht:             GPIO2  # GPIO2  D2  - DHT22 (AM2302) data pin
pin_post_enable:     GPIO21 # GPIO21 D3  - HIGH to post to Datacake, LOW to only log
pin_reset_button:    GPIO22 # GPIO22 D4  - Reset button (active LOW)
pin_ultrasonic_tx:   GPIO18 # GPIO18 D10 - Ultrasonic Tx/Echo
pin_ultrasonic_rx:   GPIO20 # GPIO20 D9  - Ultrasonic Rx/Trig
```

- `GPIO21` is used as a post-enable switch: when HIGH the device sends data to Datacake, when LOW it only logs the JSON payload for debugging.
- `GPIO22` is configured as an active-low reset button that triggers a device restart.

## Enclosure and Installation

### Enclosure Design

The ESP32 and sensors are housed in a waterproof enclosure to protect them from the elements:

![ESP32 in Enclosure](/docs/images/esp32-in-enclosure.png)
*ESP32-C6 board mounted in the waterproof enclosure*

### Stand and Mounting

The system includes a custom stand for proper positioning above the water tank:

![Stand and Enclosure 1](/docs/images/stand-and-enclosure-1.png)
*Front view of the stand and enclosure assembly*

![Stand and Enclosure 2](/docs/images/stand-and-enclosure-2.png)
*Side view of the stand and enclosure assembly*

![Stand and Enclosure 3](/docs/images/stand-and-enclosure-3.png)
*Bottom view showing the ultrasonic sensor mounting*

## Dashboard and Visualization

### DataCake Dashboard

The system sends data as JSON via HTTPS requests to a DataCake dashboard for visualization and monitoring:

![DataCake Dashboard](/docs/images/datacake-dashboard.png)
*DataCake dashboard showing water level, temperature, humidity, and battery status*

## Technical Specifications

### Power Consumption

- **Active Mode**: ~80mA
- **Deep Sleep**: ~0.1mA
- **Measurement Cycle**: ~5 seconds
- **Battery Life**: 3-4 months with 2000mAh LiPo battery (60-minute intervals, not verified yet)

### Measurement Specifications

- **Water Level Range**: 0-300cm (adjustable in configuration)
- **Temperature Range**: -40°C to 80°C
- **Humidity Range**: 0-100% RH
- **Measurement Accuracy**: ±1cm for water level, ±0.5°C for temperature

### ESPHome Integration

<img src="images/made-for-esphome-white-on-black.png" title="Made for ESPHome" alt="Made for ESPHome Logo" width=150>

---

For more information about the project setup, configuration, and usage, please refer to the main [README.md](../README.md) file.