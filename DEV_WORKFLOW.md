# Development Workflow

This document describes the recommended workflow for modifying the Passbox Controller Emulator.

---

# 1. Branching Strategy

All changes must be implemented in a feature branch.

Example:

git checkout -b feature-pressure-logic

Direct modifications in main are discouraged.

---

# 2. Implementation

When implementing a feature:

1. read SYSTEM_ARCHITECTURE.md
2. read CONTROL_ALGORITHM.md
3. follow AI_RULES.md

Only modify required JavaScript logic.

Avoid changing HTML structure.

---

# 3. Testing

After modification verify:

- emulator start button works
- pressure simulation updates
- alarms trigger correctly
- charts update
- door interlock works

---

# 4. Commit Rules

Commits must describe the change.

Examples:

Added pressure priority logic  
Fixed emulator start bug  
Improved alarm delay logic

Avoid vague messages like:

update  
fix

---

# 5. Merge Process

After testing:

1. merge feature branch into main
2. push changes

Example:

git checkout main  
git merge feature-pressure-logic  
git push

---

# 6. Safety

Before modifying code:

check for existing functions.

Avoid:

duplicate timers  
duplicate global variables  
renaming UI handlers

---

# 7. Documentation

When implementing major logic:

update documentation inside the docs/ folder.