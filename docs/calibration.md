# Calibration Notes

## Pulse timing

The first firmware version should start with conservative pulse lengths.

Example starting range:

```text
10 ms
20 ms
30 ms
40 ms
50 ms
```

For 50 Hz mains, one half-cycle is 10 ms. The firmware can count zero-cross events and fire the triac for the required number of half-cycles.

## Test process

1. Start with no battery connected.
2. Test with scrap nickel strip.
3. Increase pulse time gradually.
4. Check weld strength by peeling the strip.
5. Stop increasing once the weld is strong and the strip is not badly burned.

## Notes

- Different nickel strip thicknesses need different pulse energy.
- Electrode pressure strongly affects weld quality.
- Dirty or oxidized electrodes make welds worse.
- Electrode tips should be cleaned and reshaped when needed.
