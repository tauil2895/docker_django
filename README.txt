key
7dd5ddd90e7f7fdeffec09356655e43aab9c651b45c72caceb6a0ba3aa0f66d5

Download venv package
python -m venv venv

For Windows cmd
.\venv\Scripts\activate.bat

Install Django
python -m pip install Django

Start a new Django Project
django-admin startproject config .

Run Server
python manage.py runserver

Create Docker File
Dockerfile

Copy and prepare Docker File
FROM python:3.14.3-alpine3.23
ENV PYTHONUNBUFFERED=1
WORKDIR /app

Run and install some packages to Docker
RUN apk update \
    && apk add --no-cache gcc musl-dev postgresql-dev python3-dev libffi-dev \
    && pip install --upgrade pip

COPY ./requirements.txt ./

RUN pip install -r requirements.txt

COPY ./ ./

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]

Run the dockerfile onto the docker_django
docker built -t devrrior/docker_django .

Run docker server
docker run -p 8000:8000 devrrior/docker_django
or
docker run -v /c/projects/docker_django/:/app -p 8000:8000 devrrior/docker_django

Enter to the docker bash to migrate DB
docker exec -it Number ID /bin/sh

Migrate DataBase
python manage.py migrate

Create superuser for a Django Admins Portal Database
python manage.py createsuperuser
python manage.py runserver

### Give a fix name to the docker container
docker exec -it <nombre_contenedor> gunicorn myproject.wsgi:application --bind 0.0.0.0:8000

### Create docker-compose.yml
Add the code to this file

### Stop docker
docker stop $(docker ps -q)

### Built Docker with the new compose file
docker-compose up --build

### Compile and run the app
docker-compose up

### Migrate and create superuser in docker-compose
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser

### Crear la aplicacion
docker-compose exec web python manage.py startapp backend

### Install git
winget install --id Git.Git -e --source winget

