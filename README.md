# YetiX-A

Small development board for the NXP MCX-A series MCUs.

YetiX-A is designed to be compact while still exposing most peripherals needed for firmware development, board bring-up, and protocol testing.

## Features

- SPI EEPROM
- SPI micro SD card slot
- CAN transceiver with optional bus termination
- USB-C connector with ISP button support
- 42 board pins exposing almost all MCU peripherals
- 10-pin ARM Cortex debug connector

## Pin Out

Most MCU pins are routed directly to board pins.

Some signals (for example SPI1 MISO, MOSI, and SCK) are internally connected to onboard peripherals and are still exposed as board pins. Other signals (for example debug pins and chip select lines) are only internally connected and not exposed.

For the exact mapping of MCU pins to board pins, see:

- [assets/PIN_Functions.csv](assets/PIN_Functions.csv)

## Quick Start

1. Power the board via the USB-C receptecal or the 5V Pin
2. Connect a debugger to the 10-pin Cortex debug header, or use ISP mode over USB.
3. Flash a minimal firmware project (for example, a GPIO blink) to verify toolchain and board bring-up.

## Programming And Debug

### SWD/JTAG Debug Header

YetiX-A includes a 10-pin ARM Cortex debug connector for standard MCU debugging workflows.

Recommended usage:

1. Power the board from USB-C or the intended external source.
2. Connect your debug probe to the Cortex header.
3. Use your preferred IDE/debug server to connect and flash.

### USB ISP Mode

The board supports ISP using the USB-C interface.

Typical flow:

1. Hold the ISP button.
2. Connect USB or reset the target if already connected.
3. Release the button.
4. Drag and drop the .uf2 file to the mass storage device.

## Onboard Peripherals

### SPI EEPROM (ST M95256-DF)

- Intended for non-volatile parameter/configuration storage.
- Shares SPI1 bus with SD-card and other externally connected devices.

### SPI micro SD Slot

- Intended for logging, file storage, or data exchange.
- Shares SPI1 bus with EEPROM and other externally connected devices.
- Switch to detect card insertion.

### CAN Transceiver (NXP TJA1042BT)

- 5V CAN Transceiver
- Optional footprints for termination.

## Documentation And Design Files

### KiCad Source

- Schematic: [YetiX-A_DevBoard.kicad_sch](YetiX-A_DevBoard.kicad_sch)
- PCB: [YetiX-A_DevBoard.kicad_pcb](YetiX-A_DevBoard.kicad_pcb)
- Project: [YetiX-A_DevBoard.kicad_pro](YetiX-A_DevBoard.kicad_pro)

### Exported Documentation

- Schematic PDF: [FabData/YetiX-A_Schematic.pdf](FabData/YetiX-A_Schematic.pdf)
- PCB layout PDF: [FabData/YetiX-A_PCB_Layout.pdf](FabData/YetiX-A_PCB_Layout.pdf)

### Manufacturing Outputs

All Documents for fabrication can be found in [FabData](FabData)


## Hardware Revisions

| Revision | Date | Notes |
| --- | --- | --- |
| 0.0.1 | - | Initial production package |
| 0.0.2 | - | Added optional CAN Termination |

## License

See [LICENSE](LICENSE).
