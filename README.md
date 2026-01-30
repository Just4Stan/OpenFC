# OpenFC

Open-source Betaflight flight controller with integrated break-off ELRS receiver, based on the RP2354A microcontroller.
<img width="1525" height="519" alt="Screenshot 2026-01-18 at 21 32 46" src="https://github.com/user-attachments/assets/d9c790f6-fd75-4f72-9c20-73d8c4dd3b92" />

## Features

### Microcontroller
- **RP2354A** - Raspberry Pi dual-core ARM Cortex-M33 @ 150MHz (with integrated flash)
- USB-C connectivity for configuration and firmware updates

### Integrated ELRS Receiver (Break-off)
- On-board 2.4GHz ExpressLRS receiver module
- Break-off design allows for different placement if needed
- Ceramic Antenna integrated

### Sensors
- **IMU**: LSM6DSV16XTR - 6-axis accelerometer + gyroscope (SPI interface)
  - Dedicated filtered 3.3V power rail for noise isolation

### Blackbox Data Logging
- **W25Q128JVPIQTR** - 128Mbit (16MB) SPI flash for flight data recording

### Motor Outputs
- 4x PWM/DShot motor outputs (M1-M4)

### Connectivity
- **USB-C** - Configuration and firmware flashing
- **UART0** - Serial RX/TX (ELRS connection pads)
- **UART1** - Spare serial port
- **UART3** - ESC telemetry input
- **PIO UART** - Software UART via RP2350 PIO
- **I2C** - External sensor expansion
- **SPI** - Shared bus for IMU and blackbox flash

### Analog Inputs
- Current sensor input (ADC)
- RSSI input (ADC)

### Additional Features
- Addressable LED strip output (WS2812/NeoPixel)
- Buzzer output
- 16 LED's built in on corners
- ELRS ESP flashable by the RP2354A (BOOT/EN pins connected)

### Power
- 2S-6S batteries
- 10V and 5V regulated outputs
- Dedicated 3.3V_GYRO rail with additional filtering

## Repository Structure

```
OpenFC/
├── README.md
├── .gitignore
├── hardware/          ← KiCad project, libraries, and production files
│   ├── OpenFC.kicad_pro
│   ├── *.kicad_sch    ← Hierarchical schematics
│   ├── OpenFC.kicad_pcb
│   ├── lib.kicad_sym  ← Custom symbol library
│   ├── lib.pretty/    ← Custom footprint library
│   ├── lib.3dshapes/  ← 3D models
│   ├── production/    ← Gerbers, BOM, positions (all versions)
│   └── tools/         ← Analysis scripts
└── images/            ← Board renders
```

## Schematic Hierarchy

- `OpenFC.kicad_sch` - Top-level schematic
- `rp2350a.kicad_sch` - RP2354A microcontroller and supporting circuitry
- `elrs.kicad_sch` - ELRS 2.4GHz receiver module (break-off section)
- `Radioschematic.kicad_sch` - Radio/RF detailed schematic
- `power.kicad_sch` - Power supply and regulation
- `imu.kicad_sch` - LSM6DSV16XTR IMU
- `baro.kicad_sch` - BMP388 barometer
- `compass.kicad_sch` - LIS3MDLTR magnetometer (not populated, but there's space for it)
- `blackbox.kicad_sch` - W25Q128 flash memory
- `leds.kicad_sch` - Status LEDs
- `osd.kicad_sch` - OSD circuitry
- `connectors.kicad_sch` - External connectors
- `pads.kicad_sch` - Solder pads and test points

## Design Files

This project uses **KiCad 9.0** for schematic and PCB design. All symbol, footprint, and 3D model libraries are included in the repository — no external library setup is required.

## License

This project is open-source hardware. See LICENSE file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.
