# task reminder microservice


## overview

This microservice allows users to schedule, update, retrieve, and delete task reminders. It uses FastAPI for handling API requests, PostgreSQL for database storage, Celergy for background task scheduling, and Redis as the task broker.

## how to start the microservice

### 1. prerequisites
* install **Docker**, **PostgreSQL**, and **Redis**
* instal dependencies: <br /> pip install fastapi pydantic celery redis uvicorn requests sqlalchemy psycopg2

### 2. start services
* start **PostgreSQL**: docker start postgres-container
* start **Redis**: docker start redis-container
* apply database migrations: python -c "from taskScheduler import Base, engine; Base.metadata.create_all(bind=engine)"
* start **Celery** worker: celery -A taskScheduler.celery worker --loglevel=info --pool=solo
* start **FastAPI**: uvicorn taskScheduler:app --reload

## API endpoints

### 1. schedule a reminder
  * endpoint: POST /api/reminders
  * request body:
    {
      "task_id": 1,
      "title": "Team Meeting",
      "due_date": "2025-02-25",
      "priority": "High",
      "notify_time": "2025-02-24T10:00:00"
    }
  * response:
    { "status": "Reminder scheduled", "task_id": 1 }

### 2. update a reminder
  * endpoint: PUT /api/reminders/{task_id}
  * request body:
    {
      "task_id": 1,
      "title": "Updated Meeting",
      "due_date": "2025-02-26",
      "priority": "Medium",
      "notify_time": "2025-02-25T09:00:00"
    }
  * response:
    { "status": "Reminder updated", "task_id": 1 }

### 3. get all reminders
  * endpoint: GET /api/reminders
  * request body:
    [
      {
        "title": "Updated Meeting",
        "priority": "Medium",
        "task_id": 1,
        "id": 1,
        "due_date": "2025-02-26",
        "notify_time": "2025-02-25T09:00:00"
      }
    ]
  * response:
    { "status": "Reminder updated", "task_id": 1 }


