## Generate a new keymap

Go to the [qmk configurator](https://config.qmk.fm/#/lily58/rev1/LAYOUT).

Load the previous keymap from the json folder in this directory:

```
cd ~/open-source/qmk_firmware/keyboards/lily58/keymaps/bjp
```

Download a new copy after updats and move it to the folder above.

```
mv ~/Downloads/lily58_rev1_bjp-2024-07-08-mirror-ergodox.json .
```

Generate the raw keymap with this command

```
qmk json2c lily58_rev1_bjp-2024-07-08-mirror-ergodox.json > keymap-raw.c
```

Copy the 4 layer lines to the new keymap.c

```
nvim keymap-raw.c keymap.c
```

Compile the new keymap:

```
cd ~/open-source/qmk_firmware
qmk compile --keyboard ~/open-source/qmk_firmware/keyboards/lily58 --keymap bjp -e CONVERT_TO=elite_pi
```

Double click the reset button and then you can load the firmware by mounting the microcontroller as a USB drive and copying the `.uf2` created in the last step to the microcontroller. It will reset and unmount.

On MacOS, I have to open "Disk Utility" and then right-click, click "Show in Finder on "RPI-RP2" to be able to copy a file to the microcontroller. This should be done on both halves of the keyboard.
