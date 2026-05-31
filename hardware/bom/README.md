# Bill of Materials

This folder is for BOM exports, ordering notes, and part substitutions.

## Current selected parts

### Logic PCB

| Ref | Qty | Value | Selected part |
| --- | ---: | --- | --- |
| U1 | 1 | ATmega328P-A | ATMEGA328P-AN, TQFP32 |
| U2 | 1 | MOC3023M | MOC3023M-ONS |
| U3 | 1 | H11AA1 | H11AA1 |
| Y1 | 1 | 16 MHz | 16.00M-HC49-S |
| C1-C4, C6 | 5 | 100 nF | 0603 MLCC, already available |
| C5 | 1 | 470 uF 16 V | SC1C477M08010VR |
| C7-C8 | 2 | 22 pF | GCM1885C2A220FA16D |
| R1, R3 | 2 | 10 kΩ | CRCW060310K0FKEA |
| R2 | 1 | 220 Ω | CRCW0603220RFKTABC |
| R5-R6 | 2 | 100 kΩ | CRCW2512100KFKEG |
| BZ1 | 1 | passive buzzer | 12 mm, RM7.6 |
| J1 | 1 | buttons terminal | 282836-5 |
| J2 | 1 | AVR ISP | 2x3 2.54 mm header |
| J3 | 1 | 5 V power terminal | 282836-2 |
| J4 | 1 | OLED header | 1x4 2.54 mm header |
| J6 | 1 | HV terminal | 282836-4 |

### External power module

| Item | Qty | Value | Selected part |
| --- | ---: | --- | --- |
| Triac | 1 | 800 V 41 A | BTA41-800BRG |
| Heatsink | 1 | triac heatsink | PR32/38.1/SE |
| Gate resistor | 1 | 360 Ω 2 W | PMR2S-360R |
| MOV | 1 | 275 VAC | SIOV-S14K275 / B72214S0271K101 |
| Snubber capacitor | 1 | 10 nF X2 310 VAC | JFW-10N/310-P15 |
| Snubber resistor | 1 | 47 Ω 2 W metal oxide | MOF2WS-47R |
| Foot switch | 1 | TFS-202 | TFS-202 |
| Panel buttons | 3 | momentary | PBS-20B-2 |

## Still to decide

- Fuse holder type.
- Final fuse value, likely T16A 250 VAC slow-blow after testing.
- Enclosure, strain relief, mains connector, PE grounding method.
- Electrode holder and copper electrode geometry.
