# Bring-Up Checklist

## Before power

- Inspect solder joints.
- Check for shorts between +5V and GND.
- Check orientation of electrolytic capacitor.
- Check ATmega orientation.
- Check MOC3023 and H11AA1 orientation.
- Check that HV and LV areas are separated.
- Confirm no GND plane is under the HV section.

## Low-voltage test

1. Set bench supply to 5 V with current limit.
2. Power only the logic board.
3. Verify +5 V on VCC and AVCC.
4. Verify reset pull-up.
5. Program MCU through ISP.
6. Test OLED.
7. Test buttons.
8. Test buzzer.
9. Test foot switch input.

## Clock and fuse bits

The board uses a 16 MHz external crystal. Program clock fuse bits only after the crystal and capacitors are soldered.

Planned settings:

```text
Clock: external full swing crystal
Frequency: 16 MHz
BOD: 4.3 V recommended
```

## Zero-cross test

- Test with proper isolation and safety precautions.
- Verify ZERO_CROSS on PD2 / INT0.
- Signal should switch cleanly between logic LOW and HIGH.

## Triac test

1. Test MOC output without MOT first.
2. Use a safer dummy load before the transformer.
3. Check that the triac fires only when commanded.
4. Monitor the 5 V rail during switching.
5. Confirm MCU does not reset during pulses.

## MOT test

Only test the MOT after:

- Fuse installed.
- MOV installed.
- Snubber installed.
- Triac mounted on heatsink.
- Enclosure prepared.
- Wiring strain relief added.
