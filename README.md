# Water Tank Level Sensor

Water tank monitoring with Seeed XIAO ESP32-C6 and AJ-SR04M

- Graf Regenwassertank (Zisterne) mit 1,5 m3

![Water Tank](images/water-tank.jpg "Water-Tank")  

image of board, dashboard, datacake dashboard

# Requirements

## Hardware 

- ESP32 programmable chip e.g. Seeed XIAO ESP32-C6 8MB https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html 
- Ultrasonic distance sensor e.g. JSN-RS04t
- Temperature & humidity sensor e.g. AM2302 

## Software 

- Python 
- PlatformIO https://platformio.org/
- Espressif https://www.espressif.com/en/products/socs/esp32
- ESPHome https://esphome.io/

## Wiring

![Breadboard of Water Tank Level](images/breadboard-water-tank-level.png "Breadboard")  
Breadboard wiring of the water tank level

## Configuration

water-tank.yaml
```yaml
  pin_battery_voltage: GPIO0  # GPIO0 D0
  pin_wakeup:          GPIO1  # GPIO1 left/bottom (only pins 0, 1, 2, 3, 4, 5, 6, 7 may support wakeup)
  pin_dht:             GPIO2  # GPIO2 D2
  pin_ultrasonic_rx:   GPIO18 # GPIO18 Rx/Trig
  pin_ultrasonic_tx:   GPIO20 # GPIO20 Tx/Echo
```

Copying `/common/secrets-template.yaml` to `/common/secrets.yaml` and configure the WiFi credentials.

## Dashboard

The dashboard was realized using DataCake (https://datacake.co/) which displays the current and past water level, battery level and the temperature and humidity.

![Dashboard](/images/dashboard.png)  
DataCake Dashboard

## Resources

- Getting Started with Seeed Studio XIAO ESP32C6, https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/

## Contact

- Autor: Roland Ortner
- Date: 2024-09-07
- LinkedIn: https://www.linkedin.com/in/roland-ortner/
- Reports: battery voltage, WiFi signal, level and volume in water tank
- Icons: https://pictogrammers.com/library/mdi/

<img src="images/made-for-esphome-white-on-black.png" title="Made for ESPHome" alt="Made for ESPHome Logo" width=150>
