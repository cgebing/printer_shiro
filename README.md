# CoreXY 3D-Printer

## File `/etc/network/interfaces.d/can0`

```
allow-hotplug can0
iface can0 can static
    bitrate 500000
    up ifconfig $IFACE txqueuelen 1024
```

## Manta M5P

### Klipper Firmware

- Processor model (STM32G0B1)
- Bootloader offset (8KiB bootloader)
- Clock Reference (8 MHz crystal)
- Communication interface (USB to CAN bus bridge (USB on PA11/PA12))
- CAN bus interface (CAN bus (on PD0/PD1))
- (500000) CAN bus speed

### Update

- DFU Mode (Hold down Boot + Press Reset)
- `make flash FLASH_DEVICE=0483:df11`

## EBB36

### Klipper Firmware

- Processor model (STM32G0B1)
- Bootloader offset (8KiB bootloader)
- Clock Reference (8 MHz crystal)
- Communication interface (CAN bus (on PB0/PB1))
- (500000) CAN bus speed

### Update

- `python3 ~/katapult/scripts/flash_can.py -i can0 -f ~/klipper/out/klipper.bin -u 467d74c5aadd`
