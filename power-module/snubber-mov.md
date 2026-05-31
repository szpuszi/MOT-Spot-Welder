# Snubber and MOV Notes

## Snubber

The snubber is a series RC network connected across the triac.

```text
MT1 -> 47 ohm 2 W -> 10 nF X2 -> MT2
```

Selected parts:

- Resistor: MOF2WS-47R, 47 ohm, 2 W, metal oxide, THT.
- Capacitor: JFW-10N/310-P15, 10 nF, X2, 310 VAC, THT.

Purpose:

- Reduce voltage spikes.
- Reduce false triggering.
- Improve triac reliability with the inductive MOT load.

## MOV

The MOV is connected across the mains input or across the primary side near the triac/MOT.

```text
L <-> MOV <-> N
```

Selected part:

- SIOV-S14K275 / B72214S0271K101, 275 VAC.

Purpose:

- Clamp high voltage spikes.
- Protect the triac and wiring from transient overvoltage.

## Placement

- Place both MOV and snubber physically close to the triac and MOT primary wiring.
- Keep connections short.
- Use insulated leads and safe spacing.
