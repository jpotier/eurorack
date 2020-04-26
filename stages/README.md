Mutable Instruments Stages multi-mode firmware
==============================================

This is a unofficial non-supported firmware for Mutable Instruments Stages. It started as a modification to let you enter and exit the "ouroboros" mode (the **harmonic oscillator** easter egg) at runtime, while the module is powered on. Then, it evolved adding the ability to enable **slower free-running LFOs** and a completely alternative mode that transforms the module into a **six identical DAHDSR envelope generators**.

⚠️ **Warning:** This firmware has **not** been tested on multiple [chained][1] modules. It could behave strangely if chained. Obviously I'm not responsible for any issue you might encounter.

[1]: https://mutable-instruments.net/modules/stages/manual/#chaining-modules


Download and installation
-------------------------

Download the **[latest WAV file from here][2]** and follow the [firmware update procedure here][3]. Source code is available [here][8].

[2]: https://github.com/joeSeggiola/eurorack/releases/latest
[3]: https://mutable-instruments.net/modules/stages/manual/#firmware
[8]: https://github.com/joeSeggiola/eurorack/tree/stages-multi/stages


Usage
-----

Hold one of the six buttons for 5 seconds to change mode. This setting is persisted when the module reboots. From left to right:

1. Segment generator
2. Segment generator
3. Segment generator
4. Segment generator with [slower free-running LFOs](#slower-free-running-lfos)
5. [Six DAHDSR envelope generators](#six-dahdsr-envelope-generators)
6. [Harmonic oscillator](#harmonic-oscillator), aka Ouroboros mode

For **segment generator** mode, refer to the official [Stages manual][4]. For the other modes, see below.

[4]: https://mutable-instruments.net/modules/stages/manual/


### Slower free-running LFOs

In this mode, Stages behaves exactly like the standard segment generator mode, except free-running LFOs (i.e. single green looping segments) are [eight time slower][5].

[5]: https://forum.mutable-instruments.net/t/stages/13643/54


### Six DAHDSR envelope generators

The module transforms into a generator of six identical envelopes. **Sliders** controls the duration (or level) of each stage of all envelopes. From left to right:

1. Duration of the **delay** phase
2. Duration of the **attack** phase
3. Duration of the **hold** phase
4. Duration of the **decay** phase
5. Level of the **sustain** phase
6. Duration of the **release** phase

Each duration goes from 0 to 10 seconds. Each value can be **modulated** using **TIME/LEVEL** inputs. The hold phase is always at maximum level (8V). Each stage can be "disabled" by setting the slider to the bottom; the LED on the slider will turn off to indicate that. For example, set sliders 1 and 3 to zero to get six standard ADSR envelopes.

**SHAPE/TIME** pots 1, 3 and 5 control the **shape** of the corresponding ramp stages, from accelerating through linear, to decelerating. Pots 2, 4 and 6 are unused.

**GATE** inputs are used to activate each of the six envelopes, which can be taken from the corresponding outputs on the bottom of the module.

LEDs below pots show the current phase of each envelope: green for delay/attack/hold/decay, orange for sustain, red for release, off when idle. Pressing a **button** will trigger the corresponding envelope manually, like it's a gate signal.


### Harmonic oscillator

This mode was normally accessible on the non-modified firmware by [chaining][1] the module with itself (hence the name "Ouroboros" mode). This firmware simply adds the ability to switch at runtime, without using the cable on the back of the module. All credits goes to [Stages author][9], obviously.

[9]: https://github.com/pichenettes

The left-most column of the module acts a little different from the others:

- Slider is for **coarse tuning** of the main oscillator
- Pot is for **fine tuning**
- CV is a **1V/oct** input for the root pitch
- Output is an **audio mix** of all the harmonics

Each one of the next five columns controls an additional ratio of the harmonic serie:

- Pot selects the **harmonic ratio** in relation to the root pitch
- Slider and CV input control its **volume** in the mix
- Gate is for **strumming**, i.e. temporarily increase the volume with a fast decay envelope

The **buttons** cycle through different waveform for each harmonic, including the root one. Selected waveform is shown using LEDs colors:

- Green: **sine**
- Orange: **triangle**
- Red: **square**
- Flashing green (long-press): **sawtooth**
- Flashing orange: square with **small pulse width**
- Flashing red: square with **smaller pulse width**


Feedback
--------

Please [let me know][6] if you encounter [issues][7] with my firmware modifications, or if you have ideas for additional modes.

[6]: https://github.com/joeSeggiola/eurorack/issues/new
[7]: https://github.com/joeSeggiola/eurorack/issues
