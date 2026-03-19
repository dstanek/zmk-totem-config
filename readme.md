# My Keyboard Config

TOTEM is a 38 key column-staggered split keyboard. I purchased mine from [KeyboardHoarders](https://keyboard-hoarders.com/products/totem-wired-split-keyboard-night).

## My Keymap

![My Keymap](./keymap-drawer/totem.svg?raw=true "Keymap Representation for Totem wireless")

## To flash:

1. Download firmware in actions tab
2. Keep both halves powered on
3. Plug in left half and press reset button twice quickly.  This will open up a directory on your computer.
4. Drag and drop settings reset file onto left half
5. Unplug left and plug in right side press reset twice quickly. This will open a directory on your computer.
6. Drag and drop the settings reset file onto the right half
7. Unplug right half and plug in left half again
8. Press settings reset twice
9. Drag and drop the totem left firmware file
10. Unplug left and plug in right 
11. Press reset twice
12. Drag and drop the totem right firmware file.
13. Unplug right 

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/docs/images/TOTEM_logo_bright.svg">
  <source media="(prefers-color-scheme: light)" srcset="/docs/images/TOTEM_logo_dark.svg">
  <img alt="TOTEM logo" src="/docs/images/TOTEM_logo_dark.svg">
</picture>

## ZMK CONFIG FOR THE TOTEM SPLIT KEYBOARD

- [Here](https://github.com/GEIGEIGEIST/totem) you can find the hardware files and build guide.
- [Here](https://github.com/GEIGEIGEIST/qmk-config-totem) you can find the QMK config for the TOTEM.

## HOW TO USE

- On the GitHub page of your fork navigate to "Actions"
- Scroll down and unzip the `firmware.zip` archive that contains the latest firmware
- Connect the left half of the TOTEM to your PC, press reset twice
- The keyboard should now appear as a mass storage device
- Drag'n'drop the `totem_left-seeeduino_xiao_ble-zmk.uf2` file from the archive onto the storage device
- Repeat this process with the right half and the `totem_right-seeeduino_xiao_ble-zmk.uf2` file.
