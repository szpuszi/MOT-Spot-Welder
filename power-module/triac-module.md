# Triac Power Module

The BTA41 triac is mounted outside the logic PCB, close to the MOT primary wiring.

## Selected parts

| Function | Part |
| --- | --- |
| Triac | BTA41-800BRG |
| Heatsink | PR32/38.1/SE |
| Gate resistor | PMR2S-360R, 360 ohm, 2 W |
| MOV | SIOV-S14K275 |
| Snubber capacitor | JFW-10N/310-P15, 10 nF X2 |
| Snubber resistor | MOF2WS-47R, 47 ohm, 2 W |

## Wiring

```text
L -> fuse -> MT2 BTA41
MT1 BTA41 -> MOT primary -> N

TRIAC_GATE from logic PCB -> 360R -> GATE BTA41
TRIAC_MT2 from logic PCB -> MT2 BTA41
```

## Mounting notes

- Mount the BTA41 on the heatsink.
- Keep the 360 ohm gate resistor close to the BTA41 gate pin.
- Keep the snubber and MOV close to the triac and MOT primary wiring.
- Keep power wiring short and mechanically secured.
- Keep logic wires away from MOT secondary cables.
