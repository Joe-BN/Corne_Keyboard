Note that though only one is wired it applies to both sides.
The a below is just to give you an idea of how the wiring works: 


---
![CoolCorne3](https://github.com/Joe-BN/Corne_Keyboard/assets/128038111/7688199c-8f62-440f-b4f6-f9bf333bbca6)

![CoolCorne4](https://github.com/Joe-BN/Corne_Keyboard/assets/128038111/e214ec64-e33a-4d36-9462-b9759ce47652)
---


Shout out to sanderg for the schematics !!!
Take a look at the link if you want to find out more about his build: (https://sanderg.nl/en/posts/how-to-split-keyboard-with-rp2040-and-kmk/)

## Note ##
In this build and others like it, I will also be using the KMK system to programme the microcontrolles.
As mentioned before, It's simplisity is attractive and allows room to experiment

Here is an example:

```python
import board

from kmk.kmk_keyboard import KMKKeyboard as _KMKKeyboard
from kmk.quickpin.pro_micro.boardsource_blok import pinout as pins
from kmk.scanners import DiodeOrientation


class KMKKeyboard(_KMKKeyboard):
    col_pins = (
        pins[19],
        pins[18],
        pins[17],
        pins[16],
        pins[15],
        pins[14],
    )
    row_pins = (
        pins[6],
        pins[7],
        pins[8],
        pins[9],
    )
    diode_orientation = DiodeOrientation.COLUMNS
    data_pin = pins[1]
    rgb_pixel_pin = pins[0]
    i2c = board.I2C

    # flake8: noqa
    # fmt: off
    coord_mapping = [
     0,  1,  2,  3,  4,  5,  29, 28, 27, 26, 25, 24,
     6,  7,  8,  9, 10, 11,  35, 34, 33, 32, 31, 30,
    12, 13, 14, 15, 16, 17,  41, 40, 39, 38, 37, 36,
                21, 22, 23,  47, 46, 45,
    ]
```
