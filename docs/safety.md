# Safety Notes

This project uses 230 VAC mains voltage and a microwave oven transformer. Both can be lethal.

## Main risks

- Electric shock from mains wiring.
- Fire from short circuits or overheated conductors.
- Burns from hot electrodes, welded metal, and the transformer.
- Eye injury from sparks.
- Damage to batteries if welding nickel strips to cells incorrectly.
- EMI problems causing controller resets or false triggering.

## Minimum safety requirements

- Use a closed enclosure.
- Add strain relief for mains and electrode cables.
- Keep the logic PCB separated from the MOT and power wiring.
- Keep HV and LV wiring separated.
- Use a grounded metal shield or partition if the PCB and MOT share one enclosure.
- Do not touch the circuit while powered.
- Discharge and unplug before changing wiring.

## PCB isolation target

- Keep HV and LV copper at least 7 mm apart where possible.
- Do not pour logic GND under the HV side.
- Use keepouts under and around the HV side of optocouplers and terminal blocks.

## Test order

1. Test the 5 V logic board only.
2. Program and verify the MCU.
3. Test OLED, buttons, buzzer, and foot switch.
4. Test zero-cross detection carefully.
5. Test triac control with a safe dummy load.
6. Only then test the MOT.
