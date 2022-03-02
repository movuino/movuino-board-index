# Movuino Package Board Manager
This repo contains the Movuino board packages customed to use Movuino into arduino Board Manager.

## Installation
Copy and paste **https://raw.githubusercontent.com/movuino/movuino-board-index/main/package_movuino_index.json** into `arduino IDE` -> `Preferences`-> `additional board manager URLs`. After that, search for ***Movuino Open Health Band*** in `Tools` -> `Board Manager` and install it.

## Create new board
In order to create a new board that could be detected on arduino Board Manager, you must follow the following steps :

+ Make your board package in the same format than [movuino-nrf52-1.0.0](https://github.com/movuino/movuino-board-index/tree/main/boards/movuino-nrf52-1.0.0) and increment the version in [plaform.txt](https://github.com/movuino/movuino-board-index/blob/main/boards/movuino-nrf52-1.0.0/platform.txt)

+ Put the board package in `.tar.bz2` archive

+ Check updates by running `python3 bpt.py check-updates`

+ Update the package with `python3 bpt.py update-index "board package name"`

+ Add your board package in [package_movuino_index.json](https://github.com/movuino/movuino-board-index/blob/main/package_movuino_index.json)

+ Remove cache files in `Arduino15`-> `Cache` folder

+ Restart Arduino

## Update board

[Update board package adafruit](https://learn.adafruit.com/using-board-package-tool-to-update-adafruit-arduino-packages?view=all)

