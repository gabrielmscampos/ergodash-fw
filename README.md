# ergodash-fw

## Setuping QMK

### Install qmk package

```python
python -m venv .venv
source .venv/bin/activate
pip install qmk
```

### Setup qmk cli

```python
qmk setup -H $(pwd)/qmk_firmware
```

## Compile a firmware

You can customize, compile and download the firmware at [config.qmk.fml](https://config.qmk.fm/#/omkbd/ergodash/rev1/LAYOUT_4key).

## Flash a firmware

Remember to flash each side of the ergodash at a time (remove TRRS cable and connect each side through USB, never remove TRRS while connected trough USB)!

```python
qmk flash -b <firmware.hex>
```

The application will wait until the keyboard enter the bootloader mode, double click the reset button on the PCB. Tip: You can watch lsb (`watch -n1 lsusb`) while double clicking the reset button, the keyboard entry will disappear and a ProMicro entry will appear which indicates the bootloader mode was successfully booted.
