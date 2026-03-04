# Emulator Passbox Controller — Architecture Rules

## Purpose
This document defines rules for modifying the emulator code.  
All contributors and AI tools (Codex, Copilot, ChatGPT) must follow these rules.

---

## 1. UI MUST NOT BE CHANGED
Do not modify:
- HTML layout
- CSS styles
- element IDs
- element classes

unless explicitly requested.

---

## 2. JavaScript modifications
JavaScript changes must be:
- minimal
- localized
- not breaking existing functions.

Never remove existing handlers like:
- startEmulator()
- updateEmulatorRoomSettings()

---

## 3. Emulator start logic
The function `startEmulator()` is critical.

Do NOT:
- rename it
- remove it
- wrap it in other functions

without explicit instructions.

---

## 4. Timers
All `setInterval` and `setTimeout` calls must:
- store references
- allow safe stopping

---

## 5. Pressure simulation
Pressure simulation must remain independent from UI display corrections.

Display corrections affect only **visual output**, not simulation values.

---

## 6. Alarms
Alarm logic must use the existing alarm system.

Do not create duplicate alarm handlers.

---

## 7. Settings
User settings must:
- be stored in variables
- optionally persist in localStorage
- not break existing inputs.

---

## 8. Visual stability
No changes to layout or element positioning are allowed.

---

## 9. Code safety
Before adding new logic:
- check existing variables
- avoid duplicate timers
- avoid global variable conflicts.

---

## 10. Testing
Any modification must not break:
- emulator start button
- chart updates
- door logic
- alarm system.
