# Signal Forge DSP

Custom four-layer mixed-signal DSP guitar pedal featuring real-time audio effects, ESP32 processing, and a PCM3060 stereo audio codec.

Designed and built for ELEC3117 at UNSW, Signal Forge DSP is a programmable guitar effects platform that converts an analogue guitar signal to digital audio, processes it in real time, and outputs the effected signal to a standard guitar amplifier.

<img width="435" height="580" alt="SignalForgeDSPInside" src="https://github.com/user-attachments/assets/5a1ba36c-3aa4-4906-ae3f-94a6904fe5a8" />
<img width="435" height="580" alt="SignalForgeDSPOutside" src="https://github.com/user-attachments/assets/1041d67d-f46e-4fa7-b220-bd809165ae14" />


## Overview

Signal Forge DSP was developed as a flexible alternative to traditional fixed-function analogue guitar pedals.

The system digitises an incoming guitar signal using a PCM3060 audio codec, processes the audio in real time on an ESP32, and converts the processed signal back to analogue audio for connection to a guitar amplifier.

The project involved mixed-signal PCB design, analogue signal conditioning, embedded firmware, digital audio communication, DSP implementation, hardware debugging, and enclosure integration.

## Features

- Custom four-layer mixed-signal PCB
- ESP32-WROOM-32UE microcontroller
- PCM3060 stereo ADC/DAC audio codec
- Real-time digital audio processing using I²S
- PCM3060 configuration using I²C
- Physical potentiometer controls
- Dual footswitch control with status LEDs
- Programmable DSP effects
- Standard guitar input and amplifier output
- USB programming interface for firmware updates

## System Architecture

The audio signal path is:

**Guitar → Analogue Input Stage → PCM3060 ADC → ESP32 DSP → PCM3060 DAC → Analogue Output Stage → Amplifier**

The PCM3060 handles analogue-to-digital and digital-to-analogue conversion while the ESP32 performs the real-time audio processing.
<img width="975" height="838" alt="BlockDiagram" src="https://github.com/user-attachments/assets/1c3ce336-69c9-45a2-a908-56907ecc51d0" />


## Hardware

The pedal is built around an ESP32-WROOM-32UE and PCM3060 stereo audio codec.

The PCB combines analogue audio circuitry, digital processing, power regulation, clock signals, and user controls on a four-layer mixed-signal board.

Key hardware includes:

- ESP32-WROOM-32UE
- Texas Instruments PCM3060 audio codec
- Analogue input and output buffering
- 9 V input power supply and onboard voltage regulation
- Six potentiometer inputs
- Two footswitches
- Two status LEDs
- USB-to-UART programming interface
- 125B enclosure

## Firmware

The firmware is written in C/C++ and handles:

- PCM3060 initialisation and configuration over I²C
- Real-time audio transfer using I²S
- Audio sample processing
- Potentiometer input sampling
- Footswitch debouncing and effect selection
- LED status indication
- DSP effect parameter control

## DSP Effects

Signal Forge supports multiple software-defined effects, including:

- Tremolo
- Overdrive
- Delay
- Chorus
- Pitch vibrato
- Pitch shifting

Because the effects are implemented digitally, the pedal can be reprogrammed with new algorithms without modifying the hardware.

## PCB Design

Signal Forge DSP was my first mixed-signal PCB and first four-layer PCB design.

The board integrates sensitive analogue guitar signals alongside high-frequency digital clocks, I²S audio signals, microcontroller circuitry, and multiple power rails.

The design required consideration of:

- Analogue and digital signal routing
- Ground return paths
- Power distribution and decoupling
- Audio clock routing
- ADC/DAC signal integrity
- Noise reduction
- Physical enclosure and connector constraints

<img width="393" height="645" alt="PCBF" src="https://github.com/user-attachments/assets/f1ffba58-0504-46fc-b29a-09802712a116" />
<img width="393" height="645" alt="PCBB" src="https://github.com/user-attachments/assets/599bee6e-9332-4de2-bf85-1aa3544ff313" />

## Testing and Results

The completed prototype successfully processed a live electric guitar signal in real time and produced an effected output through a standard guitar amplifier.

Testing included:

- Verification of power rails
- Oscilloscope measurement of MCLK, BCLK, and LRCK
- ADC and DAC signal verification
- Analogue input/output waveform testing
- Noise measurements
- Live guitar testing
- DSP effect verification

The final system achieved stable real-time audio processing with negligible perceived latency and low noise when operated through a clean amplifier channel.

## Challenges and Debugging

Several hardware and firmware issues were encountered during development, including:

- Audio codec configuration and clock synchronisation
- I²S communication debugging
- Power rail faults
- Intermittent PCB connections
- Analogue gain-stage debugging
- Noise from digital clock signals
- Audio stability issues in DSP algorithms
- Mechanical clearance between PCB-mounted connectors and the enclosure

These issues were diagnosed using oscilloscope measurements, multimeter testing, firmware instrumentation, and systematic signal-path testing.

## Future Improvements

Potential improvements include:

- Improved mixed-signal PCB layout for further noise reduction
- Revised connector placement for improved enclosure clearance
- OLED display for effect and preset information
- Preset storage
- Additional DSP effects
- Improved effect parameter control
- Further optimisation of DSP algorithms

## License

This project is released under the MIT License. See `LICENSE` for details.
