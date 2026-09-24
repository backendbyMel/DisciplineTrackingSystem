# Case Study: Discipline Tracking System

> **Live Application**: [LIVE APP URL]  
> **Repository**: [backendbyMel/DisciplineTrackingSystem](https://github.com/backendbyMel/DisciplineTrackingSystem)
**Tech Stack**: Python, Django, SQLite, PyInstaller

---

## 1. Executive Summary & Problem Statement

Educational and administrative institutions require reliable, centralized systems to log, track, and manage student disciplinary records. Relying on manual paper workflows or fragmented spreadsheets often results in delayed incident reporting, data inconsistency, and restricted visibility for administrators.

The **Discipline Tracking System** addresses this operational challenge by providing a structured web application tailored for institutional record management. Developed using Python and Django, the system centralizes discipline event logging and user access control into a maintainable data architecture.

*(Note: Specific institutional metrics and historical user volumes are not specified in the repository source).*

---

## 2. The Solution

The project delivers a modular web-based tracking application built around two primary domain modules:

* **Discipline Management (`disciplinetracking/`)**: Handles core logging, tracking, and record keeping for disciplinary entries.
* **User & Role Administration (`users/`)**: Manages user accounts, authentication, and access control.
* **Media Management (`media/`)**: Provides storage for user-uploaded media files and supporting documentation.
* **Desktop Executable Bundling (`lumbiaNHS.spec`)**: Packages the Django runtime, dependencies, and application logic into standalone executable binaries (`dist/`, `build/lumbiaNHS`), enabling local desktop deployment without requiring pre-installed Python environments on target devices.

---

## 3. Architecture & System Design Decisions

```
DisciplineTrackingSystem/
├── disciplinetracking/    # Core domain logic & discipline models
├── users/                 # Authentication & user management module
├── lumbiaNHS_2/           # Project configuration & settings module
├── media/                 # User-uploaded files directory
├── db.sqlite3             # Local SQLite database
├── lumbiaNHS.spec         # PyInstaller executable build specification
├── build/lumbiaNHS/       # Intermediate build artifacts
├── dist/                  # Output directory for compiled binaries
└── manage.py              # Django CLI utility 
```

### Architectural Decisions & Trade-offs

1. **Django Framework (`lumbiaNHS_2`, `manage.py`)** 
   * *Decision*: Selected Django to leverage its built-in object-relational mapper (ORM), session authentication, and clean app separation (`users` vs. `disciplinetracking`).
   * *Trade-off*: Provides rapid development and built-in security features, though with higher baseline memory overhead compared to lightweight microframeworks.

2. **SQLite Database Engine (`db.sqlite3`)**
   * *Decision*: Implemented SQLite as a zero-configuration, file-based database.
   * *Trade-off*: Highly suitable for local execution, desktop packaging, and single-institution deployments, but limited in write concurrency for high-volume multi-tenant cloud hosting.

3. **Standalone Binary Compilation (`lumbiaNHS.spec`, PyInstaller)**
   * *Decision*: Utilized PyInstaller specifications to compile the web application into standalone executable artifacts (`dist/`).
   * *Trade-off*: Significantly simplifies distribution to administrative personnel on local desktop hardware, though it increases compiled artifact size and requires specific build specs for updates.

---

## 4. Key Implementation Details

* **Modular Django Architecture**: Clean domain isolation between generic user management (`users/`) and business domain functionality (`disciplinetracking/`) wired through the main configuration package (`lumbiaNHS_2/`).
* **Media Asset Pipeline**: Integrated file upload support via Django's `media/` directory structure.
* **Executable Build Pipeline**: Custom specification file (`lumbiaNHS.spec`) configured to collect Django templates, static files, dependencies, and database references for binary compilation.

---

## 5. Engineering Challenges & Lessons Learned

* **Framework Packaging via PyInstaller**: Packaging full-stack web frameworks like Django into standalone executables requires resolving hidden imports, template path resolutions, and SQLite database migration references within the spec file (`lumbiaNHS.spec`).
* **Hybrid Deployment Strategy**: Designing an application that can function both as a web server (`manage.py runserver`) and as a standalone desktop binary (`dist/`) requires careful handling of relative path resolution for assets and SQLite files.

---

## 6. Future Roadmap & Technical Improvements

Based on the current codebase, recommended technical enhancements include:

* **Database Scalability**: Migrate from local SQLite (`db.sqlite3`) to PostgreSQL for production cloud deployments requiring concurrent database access.
* **Automated CI/CD Pipeline**: Implement GitHub Actions workflows for automated testing and automated PyInstaller binary compilation on commit.
* **Environment Configuration**: Externalize secret keys and settings into `.env` environment variables.
* **Automated Test Coverage**: Introduce Django test cases for `users/` and `disciplinetracking/` models, forms, and views.

---

## 7. Repository Metadata & Project Status

* **Repository**: `backendbyMel/DisciplineTrackingSystem`
* **Commits**: 3 commits
* **Stars / Forks**: 0 stars, 0 forks, 1 watcher
