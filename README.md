# OpenFC

Open-source Betaflight flight controller with integrated break-off ELRS receiver, based on the RP2350A microcontroller.
<img width="782" height="736" alt="Screenshot 2026-01-16 at 17 39 09" src="https://github.com/user-attachments/assets/6343ebe7-27f3-48dd-a6ed-db9a72e57b0d" />
<img width="880" height="830" alt="Screenshot 2026-01-16 at 17 39 18" src="https://github.com/user-attachments/assets/efcc17ff-df41-4898-b22a-6660c66cd391" />


## Features

### Microcontroller
- **RP2350A** - Raspberry Pi dual-core ARM Cortex-M33 @ 150MHz
- USB-C connectivity for configuration and firmware updates

### Integrated ELRS Receiver (Break-off)
- On-board 2.4GHz ExpressLRS receiver module
- Break-off design allows for external antenna placement or removal if using external receiver
- UART connection to flight controller

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
- 2x External ADC channels

### Additional Features
- Addressable LED strip output (WS2812/NeoPixel)
- Buzzer output
- Boot/DFU button
- On-board RGB status LEDs (WS2812B-2020)

### Power
- Wide input voltage range via battery input
- 5V and 3.3V regulated outputs
- Dedicated 3.3V_GYRO rail with additional filtering

## Schematic Hierarchy

- `OpenFC.kicad_sch` - Top-level schematic
- `rp2350a.kicad_sch` - RP2350A microcontroller and supporting circuitry
- `elrs.kicad_sch` - ELRS 2.4GHz receiver module (break-off section)
- `Radioschematic.kicad_sch` - Radio/RF detailed schematic
- `power.kicad_sch` - Power supply and regulation
- `imu.kicad_sch` - LSM6DSV16XTR IMU
- `baro.kicad_sch` - BMP388 barometer
- `compass.kicad_sch` - LIS3MDLTR magnetometer
- `blackbox.kicad_sch` - W25Q128 flash memory
- `leds.kicad_sch` - Status LEDs
- `connectors.kicad_sch` - External connectors
- `pads.kicad_sch` - Solder pads and test points

## Design Files

This project uses **KiCad 9.0** for schematic and PCB design.

### Directory Structure
- `*.kicad_sch` - Schematic files
- `OpenFC.kicad_pcb` - PCB layout
- `OpenFC.kicad_pro` - KiCad project file
- `lib.kicad_sym` - Custom symbol library
- `lib.pretty/` - Custom footprint library
- `lib.3dshapes/` - 3D models for components
- `production/` - Fabrication outputs (Gerbers, BOM, etc.)

## License

This project is open-source hardware. See LICENSE file for details.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.
