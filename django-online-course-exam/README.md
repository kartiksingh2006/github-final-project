# Django Online Course Exam

A small Django Online Course app that demonstrates course lessons and a multiple-choice practice exam. It implements the **Option 1 — AI-Graded Submission** deliverables: exam models, admin inlines, Bootstrap course detail template, submission/result views, and URL routes.

## Implemented grading criteria

| Criterion | Location |
|---|---|
| `Question`, `Choice`, `Submission` models | [`onlinecourse/models.py`](onlinecourse/models.py) |
| Admin registrations, `QuestionInline`, `ChoiceInline`, `QuestionAdmin`, `LessonAdmin` | [`onlinecourse/admin.py`](onlinecourse/admin.py) |
| Admin screenshot — Authentication and Authorization + OnlineCourse | Follow **Capture required screenshots** below |
| Bootstrap course name, lessons, questions, and choices | [`onlinecourse/templates/onlinecourse/course_details_bootstrap.html`](onlinecourse/templates/onlinecourse/course_details_bootstrap.html) |
| `submit` and `show_exam_result` views | [`onlinecourse/views.py`](onlinecourse/views.py) |
| `submit` and `show_exam_result` URL paths | [`onlinecourse/urls.py`](onlinecourse/urls.py) |
| Successful mock exam result screenshot | Follow **Capture required screenshots** below |

## Run locally

Requires Python 3.10+.

```bash
python -m venv .venv
# Windows PowerShell:
.venv\\Scripts\\Activate.ps1
# macOS/Linux: source .venv/bin/activate
python -m pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Open `http://127.0.0.1:8000/admin/`, sign in, and create a course in **OnlineCourse → Courses**. Add lessons and questions inline. Open each question to add at least two choices and mark exactly one as correct. Then open `http://127.0.0.1:8000/` and click the course. Sign in to submit the mock exam.

## Capture required screenshots

The two rubric screenshots must come from the running Django application; they should not be fabricated placeholders.

1. **`03-admin-site.png`** — Open `/admin/`. Capture the page with both **Authentication and Authorization** and **OnlineCourse** sections visible.
2. **`07-final.png`** — Submit an exam with enough correct answers to score at least 60%. Capture the result page showing **Congratulations!**, the score, and detailed answers.
3. Save the screenshots in `docs/screenshots/` and commit them to GitHub. On Windows, use `Win + Shift + S`.

## Notes

Each question contributes its configured `grade` to the maximum score. Only a choice belonging to the specific question is accepted. Result pages are restricted to the submitting student and staff users. A score of 60% or more displays the congratulations message.

The bundled settings use SQLite and a development-only secret key. Do not deploy them to production; use environment variables, disable debug, configure allowed hosts, and apply production security settings.
