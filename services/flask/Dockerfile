# pull official base image
FROM python:3.8.0

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip
COPY . /usr/src/app/
RUN pip install -r requirements.txt
