# Qualitest

# 🗂️ Workgroup Activity Scheduler

This project implements a **constraint-based and optimization-driven scheduler** for assigning activities within a workgroup.

It ensures:
- Full activity coverage
- Fair workload distribution
- Robustness to absences (vacations)
- Smooth rotation across weeks

---

# 🧠 Core Idea

Each week, the system assigns:

- **Primary** → main responsible person  
- **Secondary** → backup (if feasible)

The scheduler:
1. Generates many valid schedules
2. Scores them based on quality
3. Selects the **best schedule**

---

# 🔒 HARD CONSTRAINTS (Always Enforced)

These rules are **never violated**.

## 👤 Maximum Primary Load
- A person cannot be **Primary in more than 2 activities per week**

---

## 👥 Valid Assignments
For each activity:
- Primary ≠ Secondary  
- Both must **know the activity**

---

## 🧠 Skill Requirement
- A person can only be assigned to activities they are trained in

---

## 🏖️ Vacations / Availability
- People marked as “off” are:
  - Completely excluded from scheduling

Example:
```python
vacations = {
    1: ["Ivan"],
    2: ["Ahmed"]
}

