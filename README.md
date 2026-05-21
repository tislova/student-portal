# Bellini Course Scheduling System

[!Demo](demo.gif)

A desktop application for managing course schedules at the Bellini College, 
University of South Florida. Reads class data from Excel spreadsheets, 
persists it to SQLite, detects scheduling conflicts (time/room collisions, 
duplicate CRNs, missing fields), and provides a Tkinter GUI for the 
scheduling committee.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![SQLite](https://img.shields.io/badge/sqlite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)
![Tkinter](https://img.shields.io/badge/tkinter-FF6F00?style=for-the-badge&logo=python&logoColor=white)

## Team Project

This was a group project for a software engineering course at USF, built 
by a team of 4 students over a semester. The system models the actual 
scheduling workflow used by Bellini College's scheduling committee.

## What the System Does

The scheduling committee receives Excel spreadsheets with proposed course 
schedules each semester. Manually checking these for conflicts is slow and 
error-prone. This system automates the checks:

- **Required field validation** — Flags rows missing CRN, campus, level, subject, course number, or title
- **Duplicate CRN detection** — Identifies CRNs reused across sections
- **Same-time-same-room conflict detection** — Surfaces cases where two sections are scheduled in the same room at the same time
- **Meeting day validation** — Warns when sections meet on non-standard days (only MW, TR, F allowed for most courses)
- **Missing instructor detection** — Flags sections without an assigned instructor
- **Persistence** — Stores validated schedules in SQLite for cross-semester comparison

## Tech Stack

- **Python 3.8+** — Core language
- **SQLite** — Persistence layer (via `sqlite3` standard library)
- **openpyxl / pandas** — Excel file ingestion
- **Tkinter** — Desktop GUI

## Sample Conflict Report

A run against one semester's data produced:

- 2 missing-field errors (rows with no CRN, campus, or subject)
- 2 duplicate CRN errors
- 32 same-time-same-room warnings
- 14 meeting-day warnings
- 3 missing-instructor warnings

## Skills Demonstrated

- **Object-oriented design** — Class hierarchy with inheritance, encapsulation, single-responsibility classes
- **Domain modeling** — Translating real-world scheduling entities into clean code abstractions
- **Algorithm design** — Time-overlap detection with integer arithmetic
- **Team collaboration** — Built a cleanly-interfaced layer that integrated with database and GUI work by other team members
- **Software engineering process** — Worked with version control, code reviews, and integration cycles across a multi-person team
- **Real-world problem solving** — Modeled the actual workflow of a university scheduling committee

## Future Improvements

- Multi-day meeting time support (a single class meeting MWF at the same time, instead of separate entries)
- Property-based testing for the overlap logic
- Migration from Tkinter to a web interface (Flask) for browser access
