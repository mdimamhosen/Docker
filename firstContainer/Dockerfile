FROM ubuntu:24.04

RUN apt-get update && apt-get install -y  

RUN apt-get install -y golang

WORKDIR /app

COPY ./server.go ./server.go

CMD ["go", "run", "server.go"]

