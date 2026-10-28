# Student Performance Analysis System

A local web application for managing students, marks, attendance, and performance analysis. The backend now runs in **Python 3.10+** using only the Python standard library. The existing HTML, CSS, and vanilla JavaScript frontend is served unchanged.

## Technology

- Backend: Python 3.10+, standard library HTTP server
- Frontend: HTML5, CSS3, vanilla JavaScript
- Storage: JSON files in `data/`
- Server: `http://localhost:8080`
- External Python packages: none

## Run on Windows

Install Python 3.10 or newer, then run:

```bat
run.bat
```

The script starts the Python backend and opens the dashboard. Keep the backend console open while using the site. Alternatively, start it from the project directory:

```bat
python -m backend.main
```

Open `http://localhost:8080/dashboard`.

## Run on Linux or macOS

From the project directory:

```bash
python3 -m backend.main
```

To run the tests:

```bash
python3 -m unittest discover -s tests
```

The equivalent Make targets are `make run` and `make test`.

## Project structure

```text
StudentPerformanceSystem/
├── backend/
│   ├── main.py
│   ├── server.py
│   ├── service.py
│   └── storage.py
├── frontend/
│   ├── index.html
│   ├── dashboard.html
│   ├── students.html
│   ├── student-profile.html
│   ├── marks.html
│   ├── attendance.html
│   ├── analysis.html
│   ├── reports.html
│   ├── css/style.css
│   └── js/*.js
├── data/
├── reports/
├── tests/
├── Makefile
├── run.bat
└── README.md
```

## API

The Python backend preserves the existing routes and JSON response shapes used by the frontend:

```text
GET  /api/dashboard
GET  /api/students
GET  /api/students/:id
POST /api/students/add
POST /api/students/update
POST /api/students/delete
GET  /api/marks?student_id=...
POST /api/marks/add
POST /api/marks/update
POST /api/marks/delete
GET  /api/attendance?student_id=...
POST /api/attendance/add
POST /api/attendance/update
POST /api/attendance/delete
GET  /api/analysis/:id
GET  /api/reports/student/:id
GET  /api/reports/class
GET  /api/reports/subject?subject=...
```

The backend also serves the existing frontend pages at `/dashboard`, `/students`, `/student-profile`, `/marks`, `/attendance`, `/analysis`, and `/reports`.

## Data storage and reset

The application stores student, marks, and attendance records in `data/students.json`, `data/marks.json`, and `data/attendance.json`. The bundled data has been converted to JSON, preserving the existing 41 students (including the student added after the original demo seed), 320 marks records, and 320 attendance records. If the JSON files are absent on the first run, the backend seeds the 40 demo students and their related records.

To restore the demo dataset, stop the server and run `reset_demo_data.bat`, then run `run.bat` again.

## Troubleshooting

- **Python is not found:** install Python 3.10 or newer and enable the Python launcher or add Python to `PATH`.
- **Port 8080 is already in use:** stop the other server process or run `python -m backend.main --port 8081`, then open `http://localhost:8081/dashboard`.
- **The browser shows a 404:** start the server from the project directory with `run.bat` or `python -m backend.main`.

## Scope

This is a local demonstration application, not an internet-facing production deployment. It does not include user authentication or HTTPS.
