# Circuit Mono Station Sysex Messages

## Patch Dump
The following Sysex message requests a dump of the current patch information from the Circuit Mono Station.
```
F0 00 20 29 01 61 40 00 F7
```

| Hex | Description | Comment |
| :------|:-------- |:--------|
| F0 | Sysex Start | |
| 00 20 29 | Manufacturer ID | Novation |
| 01 | Novation Product Type | Synth |
| 61 | Novation Product Number | Circuit Mono Station |
| 40 | Command | Current Patch Dump Request |
| 00 | Location (?) | |
| F7 | Sysex End | |

Note that this is very close to the documented Sysex messages for the original Circuit, only the product number differs: Circuit Mono Station = 61, Circuit = 60.

## Patch Format
Following a Patch Dump Request, the Circuit Mono Station returns a 135 bytes Sysex message containing the value of all synth parameters.

| Offset | Bytes | Bits | Parameter |
| ------:| -----:| :--- | :-------- |
|      0 |     1 |   x  | Sysex Start|
|      1 |     3 |  24  | Manufacturer ID |
|      9 |    16 | 16x8 | Patch Name |
|     25 |     1 |   ?  | ??? |
|     26 |     1 |   ?  | ??? |
|     27 |     1 |   1  | Envelope Retrigger |
|     28 |    14 | 14x8 | ??? |
|     42 |     1 |   2  | Osc 1 Waveform |
|     43 |     1 |   7  | Osc 1 PWM |
|     44 |     2 |   8  | Osc 1 Coarse |
|     46 |     2 |   8  | Osc 1 Fine |
|     48 |     1 |   2  | Osc 1 Range |
|     49 |     1 |   ?  | ??? |
|     50 |     1 |   ?  | ??? |
|     51 |     1 |   2  | Osc 2 Waveform |
|     52 |     1 |   7  | Osc 2 PWM |
|     53 |     2 |   8  | Osc 2 Coarse |
|     55 |     2 |   8  | Osc 2 Fine |
|     57 |     1 |   2  | Osc 2 Range |
|     58 |     1 |   ?  | ??? |
|     59 |     1 |   1  | Osc 2 Sync |
|     60 |     1 |   ?  | ??? |
|     61 |     2 |   8  | Mixer Osc 1 |
|     63 |     2 |   8  | Mixer Osc 2 |
|     65 |     2 |   8  | Mixer Sub |
|     67 |     2 |   8  | Mixer Noise |
|     69 |     2 |   8  | Mixer Audio In |
|     71 |     2 |   8  | Mixer Ring 1-2 |
|     73 |     1 |   7  | Filter Overdrive |
|     74 |     1 |   7  | Filter Resonance |
|     75 |     2 |   8  | Filter Frequency |
|     77 |     1 |   2  | Filter Shape |
|     78 |     1 |   1  | Filter Slope |
|     79 |     1 |   2  | Filter Bypass |
|     80 |     1 |   3  | Filter Key Tracking |
|     81 |     1 |   7  | Envelope Attack |
|     82 |     1 |   7  | Envelope Decay |
|     83 |     1 |   7  | Envelope Sustain |
|     84 |     1 |   7  | Envelope Release |
|     85 |     1 |   7  | LFO Waveform |
|     86 |     2 |   8  | LFO Rate (Sync Off) |
|     88 |     1 |   5  | LFO Rate (Sync On) |
|     89 |     1 |   1  | LFO Sync |
|     90 |     1 |   1  | LFO Retrigger |
|     91 |     1 |   7  | Distortion Level |
|     92 |     1 |   2  | Distortion Type |
|     93 |     2 |   8  | Mod Env -> Osc 1 Pitch |
|     95 |     1 |   7  | Mod Env -> Osc 1 PWM |
|     96 |     2 |   8  | Mod Env -> Osc 2 Pitch |
|     98 |     1 |   7  | Mod Env -> Osc 2 PWM |
|     99 |     1 |   1  | Mod Env -> Amp |
|    100 |     2 |   8  | Mod Env -> Filter |
|    102 |     1 |   7  | Mod Env -> Distortion |
|    103 |     1 |   7  | Mod Env -> Aux CV |
|    104 |     2 |   8  | Mod LFO -> Osc 1 Pitch |
|    106 |     1 |   7  | Mod LFO -> Osc 1 PWM |
|    107 |     2 |   8  | Mod LFO -> Osc 2 Pitch |
|    109 |     1 |   7  | Mod LFO -> Osc 2 PWM |
|    110 |     1 |   7  | Mod LFO -> Amp |
|    111 |     2 |   8  | Mod LFO -> Filter |
|    113 |     1 |   7  | Mod LFO -> Distortion |
|    114 |     1 |   7  | Mod LFO -> Aux CV |
|    115 |     2 |   8  | Mod Seq -> Osc 1 Pitch |
|    117 |     1 |   7  | Mod Seq -> Osc 1 PWM |
|    118 |     2 |   8  | Mod Seq -> Osc 2 Pitch |
|    120 |     1 |   7  | Mod Seq -> Osc 2 PWM |
|    121 |     1 |   7  | Mod Seq -> Amp |
|    122 |     2 |   8  | Mod Seq -> Filter |
|    124 |     1 |   7  | Mod Seq -> Distortion |
|    125 |     1 |   7  | Mod Seq -> Aux CV |
|    126 |     1 |   7  | Mod Vel -> Osc 1 Pitch |
|    127 |     1 |   7  | Mod Vel -> Osc 1 PWM |
|    128 |     1 |   7  | Mod Vel -> Osc 2 Pitch |
|    129 |     1 |   7  | Mod Vel -> Osc 2 PWM |
|    130 |     1 |   7  | Mod Vel -> Amp |
|    131 |     1 |   7  | Mod Vel -> Filter |
|    132 |     1 |   7  | Mod Vel -> Distortion |
|    133 |     1 |   7  | Mod Vel -> Aux CV |
|    134 |     1 |   5  | Modulation Selector |
|    135 |     1 |   x  | Sysex End|
