# Passbox Controller Emulator

Web-based emulator of a cleanroom passbox controller.

The project simulates pressure control, alarms and door logic of a passbox used in pharmaceutical cleanrooms.

---

## Main Features

- Pressure difference simulation between gateway and rooms
- Priority control relative to Room 1 or Room 2 (ΔP1 / ΔP2)
- Alarm system with delay
- Door interlock logic
- HEPA filter and UV lamp control
- Pressure charts and emulator
- Parameter correction system

---

## Interface Overview

The emulator includes several panels:

### Main Panel
Displays:
- Gateway pressure
- Pressure difference with Room 1
- Pressure difference with Room 2
- Door states
- Alarm indicators

### Emulator Page
Allows simulation of:
- Room pressure changes
- Working pressure limits
- Absolute pressure limits

### Settings Page
Configuration of:
- Pressure limits
- Alarm delay
- Pressure priority
- Sterilization parameters

---

## Architecture Rules

Project structure is controlled by `ARCHITECTURE.md`.

Important rules:

- UI layout must not be modified
- Existing function names must remain unchanged
- Pressure simulation must be separated from display corrections
- Timers must be controlled safely

---

## Technology

The emulator is implemented using:

- HTML
- CSS
- JavaScript
- Chart.js

No backend is required.

---

## How to Run

Download the repository and open the main HTML file in a browser.

Example:
FinalEmulator_rebuilt_final_corr_limits.html

---

## Development

Recommended workflow:

1. Create a feature branch
2. Implement changes
3. Test emulator start and alarms
4. Merge into `main`

Example:
git checkout -b feature-pressure-logic

---

## Purpose

This emulator is used for:

- controller logic development
- testing pressure algorithms
- demonstration of passbox control systems

---

## Author

Passbox Controller Emulator project.
