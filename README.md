# RMK

Keyboard firmware for cortex-m, with layer/dynamic keymap/[vial](https://get.vial.today) support, written in Rust.

## Checklist after generating the firmware project

- [ ] Update `memory.x` for your microcontroller(if needed)

- [ ] Update your `keyboard.toml`

- [ ] Create your `vial.json` by your layout: https://get.vial.today/docs/porting-to-via.html, replace the default one

- [ ] (Optional) Check the chip name of `probe-rs` is right, if you don't use `cargo run`, you can skip this step

- [ ] Update the family ID of your microcontroller in `Makefile.toml`, if you want to generate .uf2 firmware. The available family ID can be found in `scripts/uf2conv.py`

## For BLE only

To use NRF BLE, you should have [nrf s140 softdevice 7.3.0](https://www.nordicsemi.com/Products/Development-software/s140/download) flashed to nrf52840 first. 

The following are the detailed steps:

1. Erase the flash:
   ```shell
   probe-rs erase --chip nrf52840_xxAA
   ```
2. Flash softdevice firmware to flash:
   ```shell
   probe-rs download --verify --format hex --chip nRF52840_xxAA s140_nrf52_7.3.0_softdevice.hex
   ```
3. Compile, flash and run the example
   ```shell
   cargo run --release
   ```
