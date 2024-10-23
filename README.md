# ergodash-fw

## Requirements

In case you are using Fedora 40+, you'll need to enable the `erovia/dfu-programmer` copr:

```bash
sudo dnf copr enable erovia/dfu-programmer
```

Install all requirements:

```bash
sudo dnf install arm-none-eabi-binutils-cs arm-none-eabi-gcc-cs arm-none-eabi-gcc-cs-c++ arm-none-eabi-newlib avr-binutils avr-gcc avr-gcc-c++ avr-libc avrdude clang dfu-programmer dfu-util kernel-devel bison clang-libs clang-resource-filesystem elfutils-libelf-devel flex hidapi libzstd-devel llvm compiler-rt libomp libomp-devel libusb1-devel libusb-compat-0.1-devel
```

## Setuping QMK

### Install qmk package

```bash
python -m venv .venv
source .venv/bin/activate
pip install qmk
```

### Setup qmk cli

```bash
qmk setup -H $(pwd)/qmk_firmware
```

Copy udev rules and reload:

```bash
cp $(pwd)/qmk_firmware/util/udev/50-qmk.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
```

## Compile a firmware

You can customize, compile and download the firmware at [config.qmk.fm](https://config.qmk.fm/#/omkbd/ergodash/rev1/LAYOUT_4key).

## Flash a firmware

Remember to flash each side of the ergodash at a time (remove TRRS cable and connect each side through USB, never remove TRRS while connected trough USB)!

```python
qmk flash -b <firmware.hex>
```

QMK will wait until the keyboard enter the bootloader mode, for Falbatech's ErgoDash you can double click the reset button on the PCB.

Tip: You can watch lsb (`watch -n1 lsusb`) while double clicking the reset button, the keyboard entry will disappear and a ProMicro entry will appear which indicates the bootloader mode was successfully booted.
