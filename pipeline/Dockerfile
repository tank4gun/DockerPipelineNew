# syntax=docker/dockerfile:1
FROM python:3.7-alpine
COPY godata/config/cruise-config.xml /etc/go/cruise-config.xml
RUN chown -R 999:999 /etc/go
VOLUME ["/etc/go/"]
COPY requirements.txt requirements.txt
RUN pip install --upgrade pip && pip install -r requirements.txt
