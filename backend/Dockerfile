# Derive from Debian linux (Buster) Python image, without add-ons (slim). Can be found here: https://hub.docker.com/r/library/python/tags/
FROM python:3.9-slim-buster

# Add user that runs application, and use homedir as app directory
RUN adduser backend --gecos "backend" --disabled-password
ENV HOME=/home/backend
ENV APP_HOME=/home/backend/web
RUN mkdir $APP_HOME
RUN mkdir $APP_HOME/staticfiles
RUN mkdir $HOME/media
RUN mkdir $HOME/logs
WORKDIR $APP_HOME

# Set Environmental Variables (no *.pyc files and immediately show python console output)
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Setup Virtual Environment and install dependencies
COPY requirements.txt $APP_HOME/
RUN pip install --upgrade pip && pip install -r requirements.txt

# Collect static files
# RUN python manage.py collectstatic

# Copy code
COPY . .