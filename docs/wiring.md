# Wiring Notes

## Logic board connections

### 5 V input

```text
External 5 V supply + -> J3 +5V
External 5 V supply - -> J3 GND
```

The logic supply is separate from the MOT mains wiring.

### OLED

```text
J4 +5V -> OLED VCC
J4 GND -> OLED GND
J4 SDA -> OLED SDA
J4 SCL -> OLED SCL
```

The selected OLED module already has I2C pull-up resistors.

### Buttons

The panel buttons are connected between each signal pin and GND. Firmware uses internal pull-ups.

```text
Button common -> GND
PLUS_10 -> button -> GND
MINUS_10 -> button -> GND
MODE -> button -> GND
```

### Foot switch

Use COM and NO contacts from the TFS-202 foot switch.

```text
WELD_BTN -> foot switch NO
GND -> foot switch COM
```

## Power module wiring

```text
L -> fuse -> MT2 BTA41
MT1 BTA41 -> MOT primary -> N

TRIAC_GATE from logic PCB -> 360R -> GATE BTA41
TRIAC_MT2 from logic PCB -> MT2 BTA41
```

The 360 ohm gate resistor is mounted physically near the BTA41.

## Protection parts

```text
MOV: L <-> N
Snubber: MT1 -> 47R -> 10nF X2 -> MT2
```

Keep snubber and MOV close to the triac and MOT wiring.
