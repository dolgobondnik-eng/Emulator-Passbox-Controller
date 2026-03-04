# Passbox Controller Emulator — Control Algorithm

This document describes the control algorithm of the passbox pressure controller.

The algorithm defines how the gateway chamber pressure is regulated relative to Room 1 or Room 2.

---

# 1. Control Objective

The controller maintains the pressure difference between the gateway chamber and the selected room.

Possible modes:

ΔP1 priority  
ΔP2 priority

The controller regulates gateway pressure relative to the selected room.

---

# 2. Pressure Definitions

P_room1 – pressure in room 1

P_gateway – pressure in gateway chamber

P_room2 – pressure in room 2

Pressure differences:

ΔP1 = P_gateway − P_room1

ΔP2 = P_gateway − P_room2

---

# 3. Target Range

Each room has a configured working pressure range.

Example:

Room 1 working range

ΔP1_min  
ΔP1_max

Room 2 working range

ΔP2_min  
ΔP2_max

The controller attempts to keep ΔP within the selected range.

---

# 4. Priority Mode

Priority determines which pressure difference is actively regulated.

Mode: ΔP1

Controller adjusts gateway pressure relative to Room 1.

ΔP2 becomes a secondary parameter.

Mode: ΔP2

Controller adjusts gateway pressure relative to Room 2.

ΔP1 becomes secondary.

---

# 5. Control Loop

The control algorithm runs continuously while emulator is active.

Control cycle:

1. Read current pressures
2. Calculate ΔP1 and ΔP2
3. Determine active priority mode
4. Compare pressure difference with working limits
5. Adjust gateway pressure simulation

Control loop interval:

100–500 ms

---

# 6. Regulation Strategy

The emulator uses a simplified regulation model.

If ΔP < working minimum:

increase gateway pressure

If ΔP > working maximum:

decrease gateway pressure

If ΔP is within limits:

maintain current pressure

This behaviour simulates fan airflow adjustments.

---

# 7. Alarm Conditions

Pressure alarm occurs when:

pressure difference leaves working range.

Alarm logic:

1. Detect deviation
2. Start alarm delay timer
3. If deviation persists longer than configured delay
4. Trigger alarm

If pressure returns to normal range before delay expires:

alarm timer resets.

---

# 8. Alarm Delay

Alarm delay is configured by the user.

Variable:

pressureAlarmDelay

Unit:

seconds

Purpose:

avoid false alarms caused by temporary pressure fluctuations.

---

# 9. Display Corrections

Correction parameters affect only displayed values.

They must not modify simulation values.

Corrections include:

filter correction  
ΔP1 display correction  
ΔP2 display correction

---

# 10. Emulator Stop

When emulator stops:

all timers must stop

simulation values must freeze

alarm timers must reset

---

# 11. Future Improvements

Possible future enhancements:

PID pressure regulator  
fan inertia simulation  
air leakage modelling  
sensor noise simulation

These improvements must remain compatible with existing architecture.