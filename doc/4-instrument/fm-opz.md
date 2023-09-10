# FM (OPM) instrument editor

The FM editor is divided into 7 tabs:

- **FM**: for controlling the basic parameters of FM sound source.
- **Macros (FM)**: for macros controlling algorithm, feedback and LFO 
- **Macros (OP1)**: for macros controlling FM parameters of operator 1
- **Macros (OP2)**: for macros controlling FM parameters of operator 2
- **Macros (OP3)**: for macros controlling FM parameters of operator 3
- **Macros (OP4)**: for macros controlling FM parameters of operator 4
- **Macros**: for miscellaneous macros controlling volume, arpeggio, and YM2151 noise generator.

## FM

OPZ is four-operator, meaning it takes four oscillators to produce a single sound.

These apply to the instrument as a whole:
- **Algorithm (ALG)**: Determines how operators are connected to each other (0 to 7).
  - Left-click pops up a small "operators changes with volume?" dialog where each operator can be toggled to scale with volume level.
  - Right-click to switch to a preview display of the waveform generated on a new note:
    - Left-click restarts the preview.
    - Middle-click pauses and unpauses the preview.
    - Right-click returns to algorithm view.
- **Feedback (FB)**: Determines how many times operator 1 returns its output to itself (0 to 7).

- **LFO > Freq (FMS/PMS)**: Determines how much will LFO have an effect in frequency (0 to 7).
- **LFO > Amp (AM)**: Determines how much will LFO have an effect in volume (0 to 3).
- **LFO2 > Freq (FMS/PMS2)**: Determines how much will the second LFO have an effect in frequency (0 to 7).
- **LFO2 > Amp (AMS2)**: Determines how much will the second LFO have an effect in volume (0 to 3).

- **Request from TX81Z**: if a Yamaha TX81Z is plugged in as MIDI input and output device, this sends a SysEx to the device in order to fetch its current voice.

These apply to each operator:
- The crossed-arrows button can be dragged to rearrange operators.
- **Amplitude Modulation (AM)**: Makes the operator's volume affected by LFO.
- **Attack Rate (AR)**: determines the rising time for the sound. The bigger the value, the faster the attack (0 to 31).
- **Decay Rate (DR)**: Determines the diminishing time for the sound. The higher the value, the shorter the decay. It's the initial amplitude decay rate (0 to 31).
- **Sustain Level (SL)**: Determines the point at which the sound ceases to decay and changes to a sound having a constant level. The sustain level is expressed as a fraction of the maximum level (0 to 15).
- **Decay Rate 2 (D2R) / Sustain Rate (SR)**: Determines the diminishing time for the sound. The higher the value, the shorter the decay. This is the long "tail" of the sound that continues as long as the key is depressed (0 to 31).
- **Release Rate (RR)**: Determines the rate at which the sound disappears after note off. The higher the value, the shorter the release (0 to 15).
- **Total Level (TL)**: Represents the envelope’s highest amplitude, with 0 being the largest and 127 (decimal) the smallest. A change of one unit is about 0.75 dB.

![FM ADSR chart](FM-ADSRchart.png)

- **Envelope Scale (RS/KS)**: Also known as "Key Scale" or "Rate Scale". Determines the degree to which the envelope execution speed increases according to the pitch (0 to 3).
- **Frequency Multiplier (MULT)**: Determines the operator frequency in relation to the pitch (0 to 15).
- **Fine Frequency Multiplier (Fine)**: a fine control for MULT.
- **Envelope Generator Shift (EGS)**: adds a "handicap" to the envelope. in other words, the minimum volume of the operator.
  - 0: no change
  - 1: -12dB
  - 2: -24dB
  - 3: -48dB
  - does not apply for OP4.
- **Reverb (REV)**: not a true reverb. extends release time, giving a slight reverb-like effect to the operator.
- **Fine Detune (DT)**: Shifts the pitch a little (0 to 7).
- **Waveform Select (WS)**: Changes the waveform of the operator (OPL2 and OPL3 only, 0-3 range on OPL2 and 0-7 on OPL3).
- **Coarse Detune (DT2)**: Shifts the pitch by tens of cents (0 to 3).

#### I am familiar with Yamaha TX81Z. where's LS and KVS?

these are software effects.
- you may use TL effects to simulate LS.
- you may access a KVS-like feature by clicking on the algorithm preview.

### fixed frequency mode

each operator has a Fixed Frequency mode. once enabled, the operator runs at the specified frequency regardless of the note.


## macros

Macros define the sequence of values passed to the given parameter. Via macro, along with the previously mentioned parameters, the following can be controlled:

## FM Macros

- **AM Depth**: amplitude modulation depth.
- **PM Depth**: pitch modulation depth.
- **LFO Speed**: LFO frequency.
- **LFO Shape**: LFO shape. Choose between saw, square, triangle, and random.
- **AM Depth 2**: amplitude modulation depth (second LFO).
- **PM Depth 2**: pitch modulation depth (second LFO).
- **LFO2 Speed**: LFO 2 frequency.
- **LFO2 Shape**: LFO 2 shape. Choose between saw, square, triangle, and random.

## OP1-OP4 Macros

most parameters are listed above.

## Macros

- **Arpeggio**: Pitch change sequence in semitones.
- **Noise Frequency**: specifies the noise frequency.
  - this only applies to operator 4 of channel 8!
- **Panning**: toggles output on left and right channels.
- **Pitch**: fine pitch.
  - **Relative**: when enabled, pitch changes are relative to the current pitch.
- **Phase Reset**: Restarts all operators and resets the waveform to its start. Effectively the same as a `0Cxx` retrigger.


# links

[FM instrument tutorial](https://www.youtube.com/watch?v=wS8edjurjDw): A great starting point to learn how create and work with FM sounds. This was made for DefleMask, but all the same principles apply.