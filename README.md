# PawPal+ (Module 2 Project)

You are building **PawPal+**, a Streamlit app that helps a pet owner plan care tasks for their pet.

## Scenario

A busy pet owner needs help staying consistent with pet care. They want an assistant that can:

- Track pet care tasks (walks, feeding, meds, enrichment, grooming, etc.)
- Consider constraints (time available, priority, owner preferences)
- Produce a daily plan and explain why it chose that plan

Your job is to design the system first (UML), then implement the logic in Python, then connect it to the Streamlit UI.

## What you will build

Your final app should:

- Let a user enter basic owner + pet info
- Let a user add/edit tasks (duration + priority at minimum)
- Generate a daily schedule/plan based on constraints and priorities
- Display the plan clearly (and ideally explain the reasoning)
- Include tests for the most important scheduling behaviors

## Getting started

### Setup
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### Suggested workflow

1. Read the scenario carefully and identify requirements and edge cases.
2. Draft a UML diagram (classes, attributes, methods, relationships).
3. Convert UML into Python class stubs (no logic yet).
4. Implement scheduling logic in small increments.
5. Add tests to verify key behaviors.
6. Connect your logic to the Streamlit UI in `app.py`.
7. Refine UML so it matches what you actually built.

## Features

- Add an owner profile and manage multiple pets
- Create care tasks with a scheduled time, duration, priority, and frequency
- Daily schedule sorted chronologically, with priority as a tiebreaker
- Conflict warnings when two tasks are scheduled at the same time
- Recurring tasks: marking a daily or weekly task complete automatically schedules the next occurrence
- Filter tasks by pet, completion status, or priority level

## Smarter Scheduling

The Scheduler class handles all algorithmic logic:

- Sorting: tasks are ordered by time (HH:MM), then by priority for ties
- Conflict detection: flags any two tasks scheduled at the exact same time and surfaces a warning in the UI
- Recurrence: when a daily or weekly task is marked complete, a new task is created for the next occurrence using timedelta
- Filtering: tasks can be filtered by pet name, completion status, or priority level

## Testing PawPal+

Run the test suite with:
```bash
python -m pytest
```

The suite covers task completion, recurrence logic, sorting correctness, conflict detection, filtering, and edge cases like empty owners and missing tasks.

Confidence level: 4 out of 5. Core scheduling logic is fully tested. Known gap: conflict detection checks exact time matches only, not overlapping durations.

## File structure
```
pawpal-plus/
├── pawpal_system.py    # Backend logic (Owner, Pet, Task, Scheduler)
├── app.py              # Streamlit UI
├── main.py             # CLI demo script
├── reflection.md       # Design decisions and AI collaboration notes
├── requirements.txt    # Dependencies
└── tests/
    └── test_pawpal.py  # Automated pytest suite
```