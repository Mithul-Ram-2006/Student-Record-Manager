# Student-Record-Manager

Simple CLI tool to manage student records for a school class (class 10). Records are stored in a single CSV file (students.csv). The app supports adding, viewing, updating, and deleting student records, plus a data-analytics report via the included analytics module.

##Features
- Add new student records with validation (unique student_id, non-empty fields).
- View a student's full record by student ID.
- Update math, science and english grades (grades validated to be integers between 0 and 100).
- Delete student records with confirmation.
- Run a school analytics report (invokes analytics.run_analytics_report()).

##Quick Start / Installation
1. Requirements
   - Python 3.7+ (uses only stdlib modules: csv, os)
2. Clone the repo
   - git clone https://github.com/Mithul-Ram-2006/Student-Record-Manager.git
3. Run the app
   - cd Student-Record-Manager
   - python main.py

##Usage
- The application runs as an interactive menu:
  1. Add New Student
  2. View Student Record
  3. Update Student Grades
  4. Delete Student Record
  5. Run School Analytics Report
  0. Exit

##- Prompts and validation:
  - Student ID must be unique (you are prompted to retry or cancel if it exists).
  - Student name and class/section are free-text inputs.
  - Grades must be integers between 0 and 100. Non-integer input is rejected.

##Data storage (students.csv)
- File name: students.csv (created automatically on first run if missing)
- Header (CSV columns):
  student_id, student_name, class_section, math_grade, science_grade, english_grade

##- Example CSV row:
  1001,John Doe,10-A,85,78,92

##Project structure (important files)
- main.py
  - Main CLI application, menu, and all record management functions:
    - initialize_file()
    - add_student()
    - view_student()
    - update_grades()
    - delete_student()
    - main_menu()
  - Uses students.csv for persistent storage.
- analytics.py
  - Module used by main.py to produce analytics output.
  - Invoked via analytics.run_analytics_report() from the main menu.
  - (See analytics.py to review exactly which analytics are produced and how they are formatted.)
- students.csv
  - Example / data file used by the application.

##Notes on behavior and limitations
- Single-user CLI tool: students.csv is edited directly and not designed for concurrent access.
- No authentication or encryption for the data file.
- All operations are performed in-place on the CSV file (append/write).
- There are no automated tests included in the repo.
