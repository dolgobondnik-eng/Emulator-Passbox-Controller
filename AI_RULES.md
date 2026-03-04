# AI Modification Rules

This document defines rules for AI tools modifying the Passbox Controller Emulator.

These rules apply to:

- Codex
- Copilot
- ChatGPT
- automated refactoring tools

---

# 1. Do NOT modify UI layout

Do not change:

- HTML structure
- CSS layout
- element IDs
- element classes

unless explicitly requested.

UI stability is critical.

---

# 2. Do NOT rename critical functions

The following functions must remain unchanged:

startEmulator()

updateEmulatorRoomSettings()

stopEmulator()

Renaming or removing them may break the interface.

---

# 3. Do not remove existing event handlers

Existing event handlers must remain intact.

If new logic is needed, wrap it around existing handlers.

---

# 4. Pressure simulation must remain independent

Simulation values:

pressureRoom1  
pressureGateway  
pressureRoom2  

must not be modified by display corrections.

Display corrections affect only UI output.

---

# 5. Avoid global variable conflicts

Before creating new variables:

- check existing variable names
- avoid duplicates
- avoid overwriting controller state.

---

# 6. Timers must be controlled

All timers created using:

setInterval  
setTimeout  

must store references and allow stopping.

---

# 7. Emulator start must never break

The emulator start button must always work.

Modifications must not break:

startEmulator()

---

# 8. Modify logic only

When implementing new features:

modify JavaScript logic only.

Avoid editing HTML unless required.

---

# 9. Follow architecture documentation

Always follow these documents:

SYSTEM_ARCHITECTURE.md  
ARCHITECTURE.md  
docs/CONTROL_ALGORITHM.md  
docs/STATE_MODEL.md  

---

# 10. Test after modification

After code modification verify:

- emulator start button
- pressure updates
- alarm logic
- door logic
- charts update

The system must remain operational.