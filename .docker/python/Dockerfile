FROM python:3.10-slim

ARG ENV_NAME
WORKDIR /app

RUN python3 -m pip install --upgrade pip
RUN apt-get update
RUN apt-get install ffmpeg -y


COPY requirements.txt /.tmp/requirements.txt
RUN python3 -m pip install -r /.tmp/requirements.txt

COPY ./project.pth /usr/local/lib/python3.10/site-packages
