# Passbox Controller Emulator — State Model

This document describes the state variables used by the emulator.

The state model represents the internal condition of the controller.

UI must read values from this state but must not modify simulation logic directly.

---

# 1. Pressure State

These variables represent simulated pressures.

pressureRoom1  
Pressure in room 1 (Pa)

pressureGateway  
Pressure in the passbox chamber (Pa)

pressureRoom2  
Pressure in room 2 (Pa)

---

# 2. Pressure Differences

Calculated values used for control logic.

deltaP1  
ΔP between gateway and room 1

deltaP1 = pressureGateway − pressureRoom1

deltaP2  
ΔP between gateway and room 2

deltaP2 = pressureGateway − pressureRoom2

---

# 3. Pressure Limits

Working pressure ranges configured by the user.

room1WorkMin  
room1WorkMax  

room2WorkMin  
room2WorkMax

Absolute limits:

room1AbsMin  
room1AbsMax  

room2AbsMin  
room2AbsMax

---

# 4. Priority Mode

Defines which pressure difference is actively controlled.

priorityMode

Possible values:

DP1  
DP2

When DP1 is active:

controller regulates pressure relative to room 1.

When DP2 is active:

controller regulates pressure relative to room 2.

---

# 5. Alarm System State

Alarm variables.

pressureAlarmDelay  
Delay before pressure alarm activation (seconds)

alarmActive  
Boolean value indicating active alarm condition.

alarmTimer  
Timer tracking alarm delay.

---

# 6. Device State

Simulated devices.

hepaState  
Boolean — HEPA filter running or stopped

uvLampState  
Boolean — UV lamp active

---

# 7. Door State

Door interlock system.

door1State  
door2State  

Possible values:

OPEN  
CLOSED

Door interlock prevents both doors from being open simultaneously.

---

# 8. Correction Parameters

These variables affect only UI display values.

corrFilter  
Filter pressure correction

corrDP1  
Display correction for ΔP1

corrDP2  
Display correction for ΔP2

Corrections must not modify simulated pressure values.

---

# 9. Emulator State

Global emulator state.

emulatorRunning  

Boolean value indicating whether the emulator is active.

Timers must stop when emulatorRunning becomes false.

---

# 10. State Access Rule

All state changes must be performed through controller logic.

UI must not modify state variables directly.