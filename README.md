# Hi, I'm armert

I work on embedded hardware and firmware: bootloaders, CAN and UART, flash storage, circuit design and
the measurements that prove it works. I also build test setups for it: real STM32 boards on a bench,
driven from the command line by a person or a coding agent.

Two rules run through all of it:

- **A test has to show that it can fail.** Every test is also run against something deliberately
  broken, and it must catch it. A pass that cannot fail says nothing.
- **Verdicts are for machines.** Every command returns JSON with the result and the likely causes of a
  failure, so an agent can act on it without reading a log.

## tezgah-lab

*Tezgah* is Turkish for workbench. [**tezgah-lab**](https://github.com/aarmert/tezgah-lab) is the
umbrella repo; the work lives in three repos that each stand on their own, with code, data and figures.

| Repo | What it is | Headline result |
|---|---|---|
| [**c031-ab-bootloader-stress**](https://github.com/aarmert/c031-ab-bootloader-stress) | An A/B bootloader for the NUCLEO-C031C6, reset at thousands of planned moments during a firmware update, from inside the chip and by an ESP32-S3 pulling NRST | **0 failures in 3103 trials** (95% upper bound 0.097%). The naive bootloader, as the negative control, booted a corrupt image in 11 of 20. |
| [**f407-hil-bench**](https://github.com/aarmert/f407-hil-bench) | `bench.py`: flash, reset, serial, TOML test plans and self-recovery for the STM32F407 Discovery | `smoke`, `crash_recovery`, `measure` and `camera_blink` pass on the real board, and each fails when broken on purpose |
| [**f407-camera-blink**](https://github.com/aarmert/f407-camera-blink) | Measuring an LED's blink frequency and duty cycle with a phone camera, frame by frame, against the board's own clock | 0.995 / 1.985 / 4.007 Hz for commanded 1 / 2 / 4 Hz; the board clock runs 0.5% slow |

Each repo has a "try it without hardware" section, so you can run it without a board.

## Internship

Three months in an R&D department (Sep – Nov 2026), doing the same kind of work as tezgah-lab on
real products:

- **Bootloader:** firmware updates over CAN and UART without a debug probe, taken from a dev board to
  a customer board to production firmware
- **Board bring-up:** getting a customer board to boot the app and talk CAN: a PLL setting out of
  range, a build step lost to code generation, a missing termination resistor
- **Flash storage:** settings that survive a reset, laid out so a power loss during a save keeps the
  old value, tested against simulated flash, then built into a controller's firmware
- **Sensor front-end:** photodiode and transimpedance amplifier for an optical sensor, from a Python
  radiometric model to the circuit, checked by hand and in SPICE
- **Fault finding:** a fan drawing too much power, traced on the scope to a floating PWM line and fixed
- **Evaluations:** update options for a second microcontroller family, and reverse engineering an
  undocumented high-voltage module
- **Handover:** a written guide and two talks for the team

## Elsewhere

- **RocKIT:** avionics in KIT's student hybrid-rocket team. I designed an LED driver board for the
  engine test stand in Altium and soldered it by hand.

## What I work with

**Boards** STM32F407 Discovery · NUCLEO-C031C6 · ESP32-S3<br>
**Firmware** bare-metal C, STM32 HAL and LL, bootloaders, linker scripts and flash layout, clock setup,
interrupts and ring buffers, CRC, CAN, UART, SWD<br>
**Hardware** Altium Designer from schematic to layout, SMD soldering under a microscope, photodiode
and transimpedance amplifier front-ends, PWM and MOSFET stages, SPICE<br>
**Measuring** oscilloscope, CAN bus analysis (PCAN-View), datasheet work, fault finding on real boards<br>
**Host side** Python, [uv](https://docs.astral.sh/uv/), PowerShell, TOML test plans, ffmpeg for camera measurements<br>
**Agents** Claude Code and opencode, driving the bench through `--json` output and an `AGENTS.md` per repo

## Also here

[**tiyatro**](https://github.com/aarmert/tiyatro) is my first web project, from high school in the
COVID era: HTML, CSS and Bootstrap. It is still [live](https://aarmert.github.io/tiyatro/).
