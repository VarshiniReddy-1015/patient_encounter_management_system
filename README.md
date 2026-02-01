# Medical Encounter Management System (MEMS)

A production-grade backend system built as part of the course
"Building Production-Grade Python Applications".

This project demonstrates how to design a real-world backend system that
enforces healthcare scheduling rules with timezone-safe datetime handling,
automated testing, and CI-ready workflows.

---

## Tech Stack

- FastAPI
- SQLAlchemy 2.0
- Pydantic v2
- SQLite (local) / MySQL (production)
- Poetry
- Pytest + Pytest-Cov
- Ruff, Black, Bandit
- GitHub Actions

---

## Local Setup & Testing

### 1. Install Poetry
```bash
pip3 install poetry

2. Go to project folder
cd patient_encounter_system-main

3. Install dependencies
poetry lock
poetry install

4. Activate environment
poetry env activate

Copy & paste the source command it prints.

5. Configure local database

Edit src/database.py:
DATABASE_URL = "sqlite:///./mems.db"
And update engine:
engine = create_engine(
    DATABASE_URL, connect_args={"check_same_thread": False}
)

6. Create tables
export PYTHONPATH=.
python -m src.reset_db

7. Run server
uvicorn src.main:app --reload
Open:
http://127.0.0.1:8000/docs

8. Run tests & coverage

Stop server, then:
export PYTHONPATH=.
pytest --cov=src --cov-report=term-missing --cov-fail-under=80

Features
	•	Patient management
	•	Doctor management
	•	Appointment scheduling
	•	Overlap prevention
	•	Timezone-aware datetime
	•	Domain rule enforcement
	•	90%+ test coverage