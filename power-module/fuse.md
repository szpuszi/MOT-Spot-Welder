# Fuse Notes

The mains input should include a fuse on the live conductor before the triac and MOT primary.

## Planned fuse

```text
T16A 250 VAC
5x20 mm
slow-blow / time-lag
```

`T` means time-lag / slow-blow. Do not use a fast `F16A` fuse for the MOT primary, because the transformer can create large short inrush and weld-current pulses.

## Wiring

```text
L from mains -> fuse -> MT2 BTA41
MT1 BTA41 -> MOT primary -> N
```

The fuse is not for normal short welding pulses. It is for fault conditions, for example:

- triac failed short,
- internal wiring short,
- MOT accidentally left on,
- damaged insulation,
- excessive continuous current.

## Holder

Use a proper 5x20 mm fuse holder rated for mains voltage and the required current. The holder must be enclosed and insulated so the fuse contacts cannot be touched when the enclosure is open.

## Final value

Start with T16A for the MOT spot welder power input. Final value should be verified during testing with the real transformer, wiring, triac, and pulse lengths.
