# THIS PROJECT IS STILL BEING MADE THE FILES WILL BE UPLOADED WHEN I CONNECT EVERYTHING TOGETHER, DREW SCHEMATICS FOR MOT WIRING ETC


# MOT Spot Welder Controller

Controller project for a MOT-based spot welder. The design uses an ATmega328P controller, zero-cross detection, optically isolated triac triggering, OLED UI, panel buttons, a foot switch, and an external BTA41 power triac module.

This repository is prepared for the full project files. KiCad, firmware, Gerbers, photos, and test notes can be added into the folders below.

## Main features

- ATmega328P-A in TQFP-32 package.
- 16 MHz HC-49 crystal clock.
- 5 V external logic supply.
- OLED I2C display.
- Panel buttons for mode and time adjustment.
- TFS-202 foot switch input.
- H11AA1 zero-cross detector on INT0.
- MOC3023M random-phase optotriac driver.
- External BTA41-800BRG triac power stage.
- External RC snubber and MOV protection.

## Repository structure

```text
hardware/
  kicad/          KiCad project files
  schematics/     exported schematics and PDFs
  pcb/            board screenshots, layout notes, 3D renders
  gerbers/        production Gerber files
  bom/            bill of materials and ordering notes
firmware/
  src/            firmware source code
  include/        firmware headers
  lib/            local libraries
  platformio.ini  PlatformIO configuration
power-module/
  triac-module.md power triac wiring notes
  snubber-mov.md  snubber and MOV notes
docs/
  safety.md       mains safety notes
  wiring.md       wiring plan
  bringup.md      first power-up checklist
  operation.md    UI and welding operation notes
  calibration.md  pulse timing and test notes
images/           photos, renders, diagrams
```

## System overview

The logic board does not carry the MOT welding current. It only generates control signals and reads user inputs.

The 230 VAC sensing path goes through two high-value 100 kΩ resistors into an H11AA1 optocoupler. The output side creates a ZERO_CROSS signal for the ATmega328P on INT0.

The triac drive uses a MOC3023M optotriac. The logic side is driven from the ATmega through a resistor. The high-voltage output side provides the isolated gate-drive signal for the external BTA41 triac module.

The BTA41, its heatsink, gate resistor, MOV, snubber, and MOT wiring are external to the logic PCB.

## Planned hardware

### Logic PCB

| Ref | Part |
| --- | --- |
| U1 | ATmega328P-A / ATmega328P-AN, TQFP-32 |
| U2 | MOC3023M optotriac |
| U3 | H11AA1 AC input optocoupler |
| Y1 | 16 MHz HC-49 crystal |
| C1-C4, C6 | 100 nF 0603 MLCC |
| C5 | 470 uF 16 V SMD electrolytic |
| C7-C8 | 22 pF 0603 C0G/NP0 crystal capacitors |
| R1, R3 | 10 kΩ 0603 |
| R2 | 220 Ω 0603 |
| R5, R6 | 100 kΩ 2512 |
| J1 | 5-pin button terminal |
| J2 | 2x3 AVR ISP header |
| J3 | 5 V power input terminal |
| J4 | 1x4 OLED header |
| J6 | HV/control terminal |
| BZ1 | Passive buzzer, 12 mm, RM7.6 |

### External power module

| Part | Selected component |
| --- | --- |
| Triac | BTA41-800BRG |
| Triac heatsink | PR32/38.1/SE |
| Gate resistor | PMR2S-360R, 360 Ω, 2 W |
| MOV | SIOV-S14K275 / B72214S0271K101 |
| Snubber capacitor | JFW-10N/310-P15, 10 nF, X2, 310 VAC |
| Snubber resistor | MOF2WS-47R, 47 Ω, 2 W, metal oxide |

## Pin assignment

| ATmega328P pin | Function |
| --- | --- |
| PD2 / INT0 | ZERO_CROSS |
| PC4 | OLED SDA |
| PC5 | OLED SCL |
| PC1 | TRIAC_CTRL |
| PB1 | Passive buzzer |
| PB3 | MOSI / ISP |
| PB4 | MISO / ISP |
| PB5 | SCK / ISP |
| PB6 | XTAL1 |
| PB7 | XTAL2 |
| RESET | ISP reset + 10 kΩ pull-up |

Button pins are routed to the panel terminal and are intended to use internal pull-ups in firmware.

## Power module wiring summary

```text
L -> MT2 BTA41
MT1 BTA41 -> MOT primary -> N

MOC3023 pin 4 / TRIAC_GATE -> 360R -> GATE BTA41
MOC3023 pin 6 / TRIAC_MT2  -> MT2 BTA41

MOV: L <-> N
Snubber: MT1 -> 47R -> 10nF X2 -> MT2
```

## Safety warning

This project uses 230 VAC mains voltage and a microwave oven transformer. These can be lethal and can cause fire, burns, electric shock, or equipment damage. The repository is for documentation and development only. Build and testing require proper insulation, enclosure, grounding, strain relief, and safe test procedures.

Do not touch the circuit while powered. Do not test the HV side without an enclosure and isolation-aware measurement setup.

## Bring-up plan

1. Assemble only the low-voltage logic section.
2. Power from a current-limited 5 V supply.
3. Verify 5 V, GND, reset, ISP, OLED, buttons, and buzzer.
4. Program fuse bits only after the crystal is soldered and verified.
5. Test ZERO_CROSS using a safe setup before connecting the MOT.
6. Test triac output with a resistive load or lamp before using the MOT.
7. Test MOT pulses with MOV, snubber, heatsink, and enclosure installed.

## Licensing

- Firmware is licensed under the MIT License.
- Hardware design files and hardware documentation are licensed under CERN-OHL-S-2.0.
- General documentation is licensed under CC BY 4.0 unless stated otherwise.

See `LICENSE.md` for details.
