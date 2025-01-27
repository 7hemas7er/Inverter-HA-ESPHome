# ESPHome Inverter Monitor

A project to monitor inverters through ESPHome in Home Assistant, providing real-time data monitoring.

## Prerequisites

- Home Assistant with ESPHome installed
- ESP32 (DOIT DevKit V1)
- UART connection to inverter (TX: GPIO17, RX: GPIO16)

## Features

- Real-time monitoring of inverter parameters:
  - Input/Output voltage and frequency
  - Battery voltage and charging current
  - Power metrics (apparent, active, power factor)
  - Temperature and load percentage
  - System status and operation mode

- Connectivity:
  - WiFi connectivity with fallback AP mode
  - Home Assistant API integration
  - OTA (Over-The-Air) updates support

### Optional Features
- Two relay outputs for external control (GPIO22, GPIO18)
- Status LED (GPIO2)

## Installation

1. In Home Assistant, go to ESPHome dashboard
2. Click on "+ NEW DEVICE"
3. Select your ESP32
4. Copy the provided YAML file content
5. Update WiFi credentials in your `secrets.yaml`
6. Install the firmware to your device

### Basic Configuration
```yaml
substitutions:
  name1: "inverter"
  friendly_name: "Inverter"
  tx_pin: GPIO17
  rx_pin: GPIO16
```

### WiFi Setup
Add to your ESPHome's `secrets.yaml`:
```yaml
wifi_ssid: "your_ssid"
wifi_password: "your_password"
fallback_password: "fallback_password"
```

### Relay Configuration (Optional)
If you want to add relay control, add these substitutions:
```yaml
substitutions:
  sw1_pin: GPIO22 #Relay1
  sw2_pin: GPIO18 #Relay2
```

## Communication Protocol

The device communicates with the inverter using UART with the following specifications:
- Baud rate: 2400
- Data bits: 8
- Parity: None
- Stop bits: 1
- Buffer size: 256 bytes

## Sensors

The project includes various sensor types:
- Text sensors for status information and version
- Binary sensors for system status and operation modes
- Numeric sensors for all measured values (voltage, current, power, etc.)

## Troubleshooting

- Check device logs in ESPHome dashboard
- Verify UART connections and baud rate
- Ensure proper WiFi credentials in secrets.yaml
- Monitor the "Last Response" sensor for raw communication data

## Contributing

Feel free to report issues and propose improvements.

## License

This project is open source. Feel free to use and modify as needed.
