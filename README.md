# task reminder microservice


## overview

This microservice allows users to schedule, update, retrieve, and delete task reminders. It uses FastAPI for handling API requests, PostgreSQL for database storage, Celergy for background task scheduling, and Redis as the task broker.

## how to start the microservice

1. prerequisites
* install **Docker**, **PostgreSQL**, and **Redis**
* instal dependencies: **pip install fastapi pydantic celery redis uvicorn requests sqlalchemy psycopg2**







**1. schedule a reminder**
  * endpoint: POST /api/remidners
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

## how to start the microservice
**1. schedule a reminder**
  * endpoint: POST /api/remidners
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
