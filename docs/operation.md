# Operation Notes

This file describes the intended UI behavior. Final firmware may change these details.

## Inputs

- `PLUS_10`: increase weld time.
- `MINUS_10`: decrease weld time.
- `MODE`: change mode or enter settings.
- `WELD_BTN`: foot switch input.

## Outputs

- OLED display for current mode and weld timing.
- Passive buzzer for short feedback beeps.
- TRIAC_CTRL output to the MOC3023 driver.

## Timing concept

The controller reads zero-cross pulses on `PD2 / INT0`. Weld timing should be synchronized to mains half-cycles.

For 50 Hz mains:

```text
1 half-cycle = 10 ms
2 half-cycles = 20 ms
3 half-cycles = 30 ms
```

The firmware should fire the triac only for the selected number of half-cycles. After each zero crossing, the triac must be triggered again if the weld pulse should continue.

## Suggested modes

- Manual weld.
- Single-pulse weld.
- Optional double-pulse weld.
- Settings screen.

## Buzzer feedback

Suggested signals:

- Short beep: button press.
- Double beep: weld armed.
- Long beep: weld complete.
- Error beep: invalid state or missing zero-cross.
