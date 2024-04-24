# docker-course-three-tier-web-app
This is a 3-tier web app built in Python (Flask).  There are three layers to this
application; namely:

1. `API` Layer
2. `Frontend` Layer
3. `Database - MySQL` Layer

#explanation about dockerfiles in each tire:
1. For api tier(backend tier)
Dockerfile builds an image for the API tier.
It's based on the python:3.11-slim image.
Installs system dependencies required for the Python packages using apt-get.
Copies requirements.txt to the working directory and installs Python dependencies.
Copies the rest of the application code.
Exposes port 5001 for the API.
Specifies the command to run the API application.

2. for app tier(Frontend tier)
This Dockerfile builds an image for the presentation tier (frontend).
It's also based on the python:3.11-slim image.
Copies the entire application code to the working directory.
Installs Python dependencies.
Exposes port 5002 for the frontend.
Specifies the command to run the app.

3. for database tier(db tier):
This Dockerfile builds an image for the data tier (database).
It's based on the mysql:latest image.
Sets environment variables for MySQL database configuration.
Copies the initialization SQL script init.sql to the container, which will be executed when the container starts.



We then use Docker Compose to run all of the containers at once.

## How to run these containers (using Docker Compose)
1. Make sure you have Docker Desktop running
2. Run the `docker compose build` command to build the containers
3. Run the `docker compose up -d` command to run the containers all at once
4. Open `localhost:5001/api/quotes` to see all the pre-populated sample quotes in a JSON format (assuming this is the first time you are running this).
5. On another browser, navigate to `localhost:5002` to see the frontend layer - you can add a few quotes as well as seeing other quotes coming from the database.
