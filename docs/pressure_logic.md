# Pressure Control Logic

This document describes the pressure control model of the passbox emulator.

---

## System elements

The system includes:

- Gateway chamber
- Room 1
- Room 2

Pressure is simulated for each room.

---

## Pressure differences

Pressure differences are calculated as:

ΔP1 = P_gateway − P_room1

ΔP2 = P_gateway − P_room2

---

## Priority mode

The controller can operate in two modes:

- ΔP1 priority
- ΔP2 priority

Priority defines which pressure difference is actively controlled.

---

## Control principle

When ΔP1 is selected:

The gateway pressure is adjusted relative to Room 1.

Room 2 difference becomes secondary.

When ΔP2 is selected:

The gateway pressure is adjusted relative to Room 2.

Room 1 difference becomes secondary.

---

## Alarm delay

If pressure difference leaves the working range:

1. Timer starts
2. If condition persists longer than configured delay
3. Alarm is triggered

Alarm timer resets if pressure returns to normal range.

---

## Display corrections

Display corrections affect only UI values.

They do not change simulated pressures.