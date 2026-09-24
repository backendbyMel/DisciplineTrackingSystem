# Discipline Tracking System

A Django-based web application developed by **backendbyMel** for tracking discipline records.

> **Note**: The GitHub repository source provides file and directory metadata, indicating a Django framework architecture and PyInstaller executable specifications, but does not include a detailed written project description or topic tags.

---


## 🛠 Tech Stack

* **Backend Framework**: Python / Django (`manage.py`, `db.sqlite3`)
* **Database**: SQLite (`db.sqlite3`)
* **Packaging & Executable Generation**: PyInstaller (`lumbiaNHS.spec`, `build/lumbiaNHS`, `dist/`)
* **Media Management**: Django Media directory (`media/`)

---

## 📁 Project Structure

The repository structure reflects a modular Django project architecture:

```
DisciplineTrackingSystem/
├── build/
│   └── lumbiaNHS/         # PyInstaller build cache and intermediate artifacts
├── disciplinetracking/    # Django application module for discipline tracking functionality
├── dist/                  # Output directory for compiled standalone executables
├── lumbiaNHS_2/           # Main Django project configuration and settings module
├── media/                 # Storage directory for user-uploaded media files
├── users/                 # Django application module for user management and authentication
├── db.sqlite3             # SQLite database file
├── lumbiaNHS.spec         # PyInstaller specification file for building executable binaries
└── manage.py              # Django command-line utility for administrative tasks
```

---

## 🚀 Purpose & Key Features

Based on the repository structure and Django application modules:
* **Discipline Tracking (`disciplinetracking/`)**: Core application module designed for managing and logging student/institutional discipline records.
* **User Management (`users/`)**: Application module dedicated to user handling, role management, and authentication.
* **Standalone Executable Support (`lumbiaNHS.spec`, `dist/`, `build/`)**: PyInstaller configuration allowing deployment as a standalone desktop executable (`lumbiaNHS`).
* **Local Data Persistence (`db.sqlite3`)**: Pre-configured SQLite database for local development and testing.

---

## 💻 Installation & Setup

### Prerequisites
* Python 3.x
* Git

### Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/backendbyMel/DisciplineTrackingSystem.git
   cd DisciplineTrackingSystem
   ```

2. **Run Django Development Server**:
   ```bash
   python manage.py runserver
   ```

3. **Database & Administration**:
   ```bash
   python manage.py migrate
   python manage.py createsuperuser
   ```

---

## ⚙️ Building Standalone Executable

This project includes PyInstaller specification files for compiling the Django application into a standalone executable:

```bash
pyinstaller lumbiaNHS.spec
```
Compiled output is generated in the `dist/` directory.

---

## 📊 Repository Metadata

* **Repository**: `backendbyMel/DisciplineTrackingSystem`
* **Commits**: 3 commits recorded
* **Forks / Stars**: 0 stars, 0 forks, 1 watcher
