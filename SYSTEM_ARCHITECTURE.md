# Passbox Controller Emulator — System Architecture

This document describes the architecture of the Passbox Controller Emulator.

The goal is to separate:

- UI
- Control logic
- Simulation
- Alarm system

This separation prevents breaking the interface while modifying logic.

---

# 1. System Overview

The emulator simulates a cleanroom passbox controller.

The system contains three pressure zones:

Room 1  
Gateway chamber (passbox)  
Room 2

The controller regulates the pressure inside the gateway chamber relative to one of the rooms.

---

# 2. Main Architecture Layers

The system is divided into the following layers:

UI Layer  
Controller Logic  
Pressure Simulation  
Alarm System  
Device Simulation

Diagram:

UI  
↓  
Controller Logic  
↓  
Pressure Simulation  
↓  
Alarm System

---

# 3. UI Layer

The UI layer includes:

- HTML layout
- CSS styles
- Chart.js graphs
- indicators
- buttons

Rules:

UI must not contain control logic.

UI reads values from the controller state and displays them.

---

# 4. Controller Logic

The controller layer manages system behaviour.

Responsibilities:

- pressure priority selection
- pressure regulation
- alarm delay logic
- door interlock logic

This layer decides how the system reacts to changes.

---

# 5. Pressure Simulation

The emulator simulates pressure values for:

Room 1  
Gateway chamber  
Room 2

Pressure simulation must be independent from UI corrections.

Display corrections must not affect simulated values.

---

# 6. Alarm System

The alarm system monitors:

- pressure deviations
- door violations
- abnormal states

Each alarm may have a delay before activation.

The delay prevents false alarms caused by temporary pressure fluctuations.

---

# 7. Device Simulation

The emulator simulates:

HEPA filter operation  
UV lamp  
doors  
pressure sensors

Devices update system state and may trigger alarms.

---

# 8. Timers

The system uses timers for:

pressure simulation updates  
alarm delays  
device operations

All timers must be stored and controlled centrally.

Timers must be safely stopped when emulator stops.

---

# 9. State Model

The controller maintains a global state.

Example state variables:

pressureRoom1  
pressureGateway  
pressureRoom2

deltaP1  
deltaP2

priorityMode

alarmState

UI reads values from this state.

---

# 10. Safety Rules

Never modify:

HTML layout  
element IDs  
existing event handlers

without explicit instruction.

Breaking UI bindings may disable emulator controls.

---

# 11. Development Workflow

Recommended workflow:

1. Create feature branch
2. Implement logic changes
3. Test emulator start
4. Verify alarms
5. Merge into main

Example:

git checkout -b feature-pressure-control

---

# 12. Future Improvements

Possible system improvements:

pressure regulator model  
sensor noise simulation  
fan dynamics  
airflow modelling

These improvements must remain compatible with existing architecture.