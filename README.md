# frdmn's 3D printer build log

This repository keeps track of my two 3D printer builds/changes:

- Creality Ender-3 (v1, H2 Revo direct drive extruder, dual Z, inductive ABL, soon-to-be-Klipper-machine)
- Prusa i3 MK3s clone (upgraded to Bear kit, original Prusa hotend/extruder, suffers from heatcreep/unterextrusion?)

| [![](https://up.frd.mn/c6nnbhoerK/Bildschirm-foto-2023-05-30-um-12.33.57.jpg)](#creality-ender-3-v1) | [![](https://up.frd.mn/t8n2QkA6T4/Bildschirm-foto-2023-05-30-um-12.34.05.jpg)](#prusa-i3-mk3s-clone) |
|----------|--------------|

Table Of Contents:

- [Creality Ender 3 (v1)](#creality-ender-3-v1)
  - [Hardware specs / changes](#hardware-specs--changes)
  - [3D printed modifications](#3d-printed-modifications)
  - [Firmware (Marlin)](#firmware-marlin)
    - [Specs / changes](#specs--changes)
    - [Prebuilt firmware.bin](#prebuilt-firmwarebin)
    - [Build instructions](#build-instructions)
- [Prusa i3 MK3s clone](#prusa-i3-mk3s-clone)
  - [Hardware specs / changes](#hardware-specs--changes-1)
  - [3D printed modifications](#3d-printed-modifications-1)
  - [Firmware (original Prusa)](#firmware-original-prusa)

## Creality Ender 3 (v1)

This was my very first 3D printer which now is used to try out and experiment with. It's barely a stock Ender-3 anymore (apart from it's gantry) and prints very reliable.s

### Hardware specs / changes

- Bigtreetech's [SKR Mini E3 v3](https://www.3djake.de/bigtreetech/skr-mini-e3) mainboard
- BIQU's [H2 V2S Revo](https://www.3djake.de/biqu/h2-v2s-revo-extruder) direct drive extruder
- [MAD](https://www.printables.com/model/146957-mad-modular-air-duct-for-biqu-h2-h2-v2s-revo-h2-v2) air duct with 2x 5015 blower fans
- [LJ12A3-4-Z/BX-5V](https://www.amazon.de/Taiss-induktiver-N%C3%A4herungsschalter-Arbeitsspannung-LJ12A3-4-Z/dp/B07XMND4QN/) inductive sensor (yes, there are 5V versions!)
- [Dual Z axis/motors](https://www.3djake.de/creality-3d-drucker-ersatzteile/dual-z-achsen-upgrade?sai=10662)
- BIQU's [partitioned heat bed](https://biqu.equipment/products/235mm-235mm-partitioned-hot-bed-compatible-for-ender-3-b1-hurakan)
- COMGROW's [235x235 PEI sheet](https://www.amazon.de/Comgrow-Removable-Flexible-Magnetic-Heated/dp/B09TW23M8P?th=1)
- Raspberry Pi 4 for [OctoPrint](https://octoprint.org/)
- X and Y axis belt tensioner
- builtin Raspberry Pi 4 for OctoPrint

### 3D printed modifications

- [Custom mainboard/RasPi housing](https://www.printables.com/model/464881-skr-mini-e3-v3-raspberry-pi-front-housing-for-ende)
- [MAD - Modular Air Duct for H2 V2S Revo](https://www.printables.com/model/146957-mad-modular-air-duct-for-biqu-h2-h2-v2s-revo-h2-v2)
- [Inductive probe mount for "Modular Air Duct"](https://www.printables.com/model/459319-inductive-probe-mount-for-biqu-h2-v2-v2s-revo)
- [Direct drive strain relief](https://www.printables.com/model/351250-ender-3-direct-drive-cable-bundle-strain-relief)
- [PSU Holder (For Dual Z-Rod)](https://www.printables.com/model/271707-ender-3-psu-holder-for-dual-z-rod)

### Firmware (Marlin)

#### Specs / changes

- Marlin version: [2.1.2.1](https://github.com/MarlinFirmware/Marlin/tree/2.1.2.1)
- Mesh bed leveling enabled (bilinear) using 3x3 probing grid
- Update default feedrates
- Adjusted nozzle park (G27) feature
- Default PID, E-steps, linear advance presets for direct drive extruder ([BIQU H2 V2S Revo](https://www.3djake.de/biqu/h2-v2s-revo-extruder))

#### Prebuilt firmware.bin

You can find prebuilt `firmware.bin` files under the [Releases page of this repository](https://github.com/frdmn/Marlin/releases).

#### Build instructions

If you want to build Marlin on your own, you can do so as well:

1. Clone firmware sources and this configuration repository next to each other:

    ```shell
    git clone git@github.com:MarlinFirmware/Marlin.git marlin-fw
    git clone git@github.com:frdmn/Marlin.git configuration
    ```

2. Remove the blanko default configuration files from firmware folder:

    ```shell
    rm marlin-fw/Marlin/Configuration.h
    rm marlin-fw/Marlin/Configuration_adv.h
    rm marlin-fw/Marlin/_Bootscreen.h
    rm marlin-fw/Marlin/_Statusscreen.h
    ```

3. Link custom configuration files from this repo into `marlin-fw`:

    ```shell
    ln -s configuration/config/Configuration.h marlin-fw/Marlin/Configuration.h
    ln -s configuration/config/Configuration_adv.h marlin-fw/Marlin/Configuration_adv.h
    ln -s configuration/config/_Bootscreen.h marlin-fw/Marlin/_Bootscreen.h
    ln -s configuration/config/_Statusscreen.h marlin-fw/Marlin/_Statusscreen.h
    ln -s configuration/config/platformio.ini marlin-fw/platformio.ini
    ```

4. Open `marlin-fw` in VSCode and use AutoMarlinBuild to start the build process:

    ![](https://up.frd.mn/9sxZMJvywU/Bildschirm-foto-2023-05-26-um-10.22.57.png)

## Prusa i3 MK3s clone

My second printer - Prusa i3 MK3s bear kit from Aliexpress (FSYETC store). Does print as consistent and wonderful as an original Prusa one, but suffers from sporadic heat-creep or severe underextrusion depending on the filament.

### Hardware specs / changes

- FSYETC's [MK3s bear kit](https://de.aliexpress.com/item/33030542556.html)
- Original Prusa's [MK3s hotend](https://de.aliexpress.com/item/33030542556.html) (attempt to mitigate heat creep)
- Original E3D's [non-prusa heatbreak](https://www.3djake.com/e3d/v6-heatbreak) (another attempt to mitigate heat creep)
- builtin Raspberry Pi 4 for OctoPrint

### 3D printed modifications

- [Universal Einsy Box](https://www.thingiverse.com/thing:3901001)
- [Raspberry Pi Camera Mount for Mk3S(+)](https://www.printables.com/model/64402-raspberry-pi-camera-mount-for-mk3s)

### Firmware (original Prusa)

Original Prusa firmware, [version 3.12.2](https://github.com/prusa3d/Prusa-Firmware/releases/tag/v3.12.2).
