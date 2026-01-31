# OpenFC

Open-source Betaflight flight controller with integrated break-off ELRS receiver, based on the RP2354A microcontroller.
<img width="1525" height="519" alt="Screenshot 2026-01-18 at 21 32 46" src="https://github.com/user-attachments/assets/d9c790f6-fd75-4f72-9c20-73d8c4dd3b92" />

## Features

### Microcontroller
- **RP2354B** - Raspberry Pi dual-core ARM Cortex-M33 @ 150MHz (with integrated flash)

### Integrated ELRS Receiver (Break-off)
- On-board 2.4GHz ExpressLRS receiver module
- Break-off design allows for different placement if needed

### Sensors
- **IMU**: LSM6DSV16XTR 
- **Barometer**: BMI388


### Blackbox Data Logging
- **W25Q128JVPIQTR** - 128Mbit (16MB)

### Motor Outputs
- 4x PWM/DShot motor outputs

### Analog OSD on PIO
Hardware implementation of opamp and mux to detect syncs and select between white and black pixels. Needs software implementation still.

### Connectivity
- **USB-C** - Configuration and firmware flashing
- **UART0** - Serial RX/TX (ELRS connection pads)
- **UART1** - Spare serial port
- **PIO UART** - Software UART via RP2350 PIO (2x)
- **I2C** - External sensor expansion
- **SPI** - IMU and Blackbox on isolated bus.

### Analog Inputs
- Current sensor input (ADC)
- RSSI input (ADC)
- 1 external available ADC input

### Additional Features
- Addressable LED strip output (WS2812/NeoPixel)
- Buzzer output
- 16 LED's built in on corners
- ELRS ESP flashable by the RP2354B (BOOT/EN pins connected)

### Power
- 2S-6S batteries
- 10V and 5V regulated outputs, 10V is switchable.

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
- `rp2350a.kicad_sch` - RP2354B microcontroller and supporting circuitry
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
