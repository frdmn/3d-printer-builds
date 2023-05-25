# 3D printer build log - Creality Ender 3 (v1)

This repository holds my current Marlin configuration for my Creality Ender-3 v1.

## Firmware specs / changes

- Marlin version: [2.1.2](https://github.com/MarlinFirmware/Marlin/tree/2.1.2)
- Mesh bed leveling enabled (bilinear) using 3x3 probing grid
- Update default feedrates
- Adjusted nozzle park (G27) feature
- Default PID, E-steps, linear advance presets for direct drive extruder ([BIQU H2 V2S Revo](https://www.3djake.de/biqu/h2-v2s-revo-extruder))

## Hardware specs / changes

- Mainboard: Bigtreetech's [SKR Mini E3 v3](https://www.3djake.de/bigtreetech/skr-mini-e3)
- Extruder: [BIQU H2 V2S Revo](https://www.3djake.de/biqu/h2-v2s-revo-extruder) direct drive
- Inductive sensor: [LJ12A3-4-Z/BX-5V](https://www.amazon.de/Taiss-induktiver-N%C3%A4herungsschalter-Arbeitsspannung-LJ12A3-4-Z/dp/B07XMND4QN/) (yes, there are 5V versions!)
- [Dual Z axis/motors](https://www.3djake.de/creality-3d-drucker-ersatzteile/dual-z-achsen-upgrade?sai=10662)
- BIQU's [partitioned heat bed](https://biqu.equipment/products/235mm-235mm-partitioned-hot-bed-compatible-for-ender-3-b1-hurakan)
- Raspberry Pi 4 for [OctoPrint](https://octoprint.org/)
- X and Y axis belt tensioner

## 3D printed modifications

- Custom mainboard/RasPi housing ([available on Printables](https://www.printables.com/model/464881-skr-mini-e3-v3-raspberry-pi-front-housing-for-ende))
- Inductive probe mount for "Modular Air Duct" ([available on Printables](https://www.printables.com/model/459319-inductive-probe-mount-for-biqu-h2-v2-v2s-revo))
