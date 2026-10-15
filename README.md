# E-Learn: E-Learning Database Management System

A database design and application demonstration for managing an online learning platform. E-Learn brings together users, courses, enrollments, lessons, assignments, submissions, feedback, and scores in a relational data model.

Built for **IST 659** by **Aditya Marathe, Gautam Balgi, and Rohan Gopalan**.

> **Repository status:** This repository contains the project report, presentation, Power BI report, and a recording of the Python application. The Python source, standalone SQL scripts, and Power Apps application export are not included, so cloning this repository does not provide a runnable application.

## Start here

| To understand... | Open |
|---|---|
| The problem, database design, SQL examples, and application screens | [Final project report](Final_report_submission/IST%20659%20REPORT.pdf) |
| The project presentation | [Presentation](Final_presentation.pptx) |
| The Python application's behavior | [Application recording](Python_video_app/App_working_recording.mov) |
| The analytics report | [Power BI file](PowerBI_visulizations/dbmsfinalproject.pbix) |

## What the project demonstrates

The design supports three user roles: students, instructors, and administrators. Its central workflow is straightforward:

1. An instructor creates a course and its lessons or assignments.
2. A student enrolls in a course.
3. The student submits work for an assignment.
4. The instructor records a grade and feedback.
5. Course and student performance can be queried and visualized.

The report documents three ways of interacting with the project: a Python terminal application, Power Apps screens, and Power BI dashboards. The Python demonstration includes viewing available courses, enrollment, viewing progress, and searching for courses by keyword. The Power Apps screenshots include courses, users, scores, lessons, and a calendar.

## Database design in plain language

| Entity | Purpose | Main relationship |
|---|---|---|
| Users | Store learner and instructor details and roles | Users enroll in courses and create or submit work |
| Courses | Store course titles, descriptions, and creator references | A course has enrollments, lessons, assignments, and scores |
| Enrollments | Connect students to courses | Each enrollment references a student and a course |
| Lessons | Organize course content | Each lesson belongs to a course |
| Assignments | Define work and due dates | Each assignment belongs to a course |
| Submissions | Record submitted work and grades | Each submission connects an assignment and a student |
| Feedback | Store instructor comments | Feedback references a submission and a teacher |
| Score | Record a student's score for a course | Each score references a student and a course |

Foreign keys connect these records so that, for example, a submission can be traced to its assignment, course, and student. Consult the report's logical model and SQL screenshots for the exact column names; names differ between the narrative attribute table and the implementation diagrams.

## SQL and analytics covered

The report includes screenshots of table creation, initial data, teardown scripts, queries, stored procedures, and an index. Examples include:

- Retrieving the five students with the highest scores.
- Finding courses without enrollments using a left join.
- Listing enrolled students with course details.
- Finding low scores together with student and course information.
- Retrieving courses by teacher and assignments by course through stored procedures.
- Indexing enrollments by student for lookup.

These examples show how a relational schema supports both application operations and reporting. SQL is embedded in the report as images rather than provided as executable `.sql` files.

## How to explore the repository

```bash
git clone https://github.com/gautambalgi/E-Learning-Database-Management-Sysytem.git
cd E-Learning-Database-Management-Sysytem
```

1. Read the PDF, starting with the entity descriptions and conceptual/logical diagrams.
2. Watch the recording to see the Python course-management workflow.
3. Open the presentation for an overview of the project.
4. Download the `.pbix` file and open it in Power BI Desktop. Refreshing data may require replacing the original data-source settings and supplying your own authorized database connection.

The report shows a Python client using `pyodbc` and ODBC Driver 17 for SQL Server with an Azure SQL connection. Those details describe the original implementation; they are not a complete installation procedure. Use your own database and credentials when recreating it. Connection details visible in report screenshots should not be reused or copied into new code.

## Repository layout

```text
.
├── README.md
├── Final_presentation.pptx
├── Final_report_submission/
│   └── IST 659 REPORT.pdf
├── PowerBI_visulizations/
│   └── dbmsfinalproject.pbix
└── Python_video_app/
    └── App_working_recording.mov
```

## Reproducing or extending the project

To turn the archived deliverables into a reproducible application, the missing pieces are the Python source, executable schema and seed scripts, dependency versions, and database configuration instructions. A Power Apps export would also be needed to recreate the screens directly.

Useful extensions include publishing those assets, supplying a small sample database, moving configuration into environment variables, and adding checks for enrollment, submissions, grades, and role-based access. These are next steps, not features supplied by this repository.
