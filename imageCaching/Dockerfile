FROM ubuntu:20.04

RUN apt-get update

RUN apt-get install -y curl

WORKDIR /app

COPY sample.txt /app/sample.txt

CMD ["cat", "/app/sample.txt"]
