# Movuino board index maintainer guide


## How to add a new board
1. Add your board info into `board/<board-type>/boards.txt` and update the version number in `board/<board-type>/platform.txt
1. Make sure to include the correct bootloader for your board in `board/<board-type>/bootloader`. You can either duplicate one of the bootloader for the same architecture or add a custom one. For more info to customize a bootloader see [How to customize a bootloader](#how-to-customize-a-bootloader)
1. Compress the `board/<board-type>` folder you created or modified by running `tar -jcvf <folder-path>.tar.bz2  <folder-path>`
1. Find the checksum of the archive by running `shasum -a 256 <archive-path.tar.bz2>`
1. Modify `package_movuino_index.json` with informations about the new board and add the checksum you found earlier as well as the archive size in bytes.

In order to test locally, you can spin up a local web server with python by running `python3 -m http.server` in the root of the repo.
Make sure the archives download links in `package_movuino_index.json` have been modified to use `http://localhost:8000/...`.
You can then add `http://localhost:8000/package_movuino_index.json` in the settings of the arduino and test your work.
Don't forget to erase the Arduino Cache (`~/Library/Arduino15/Cache/` on Mac) and to restart your Arduino IDE.

## How to customize a bootloader
#### Adafruit nrf52 booloaders
1. Clone [adafruit nrf52 bootloaders](https://github.com/adafruit/Adafruit_nRF52_Bootloader) repo: `https://github.com/adafruit/Adafruit_nRF52_Bootloader.git`.
2. To modify an already customized bootloader, find the patch file corresponding to the bootloader you want to edit located in the root of this repo at `bootloaders/`.
3. Go to the adafruit nrf52 bootloader repo you just cloned and run `git apply <patchfile-path>`. This will add the movuino bootloader source files to the adafruit repo.
4. Run `make BOARD=<board-source-folder-name> all` to compile the bootloader. You will need to have adafruit-nrfutils installed to created the bootloader in .zip format.
5. The compiled bootloader in .hex and .zip can then be found in `_build/`

