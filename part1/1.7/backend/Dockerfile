FROM ubuntu:16.04

WORKDIR /app
EXPOSE 8000

RUN apt-get update && apt-get install -y curl git
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
RUN apt install -y nodejs
RUN git clone https://github.com/docker-hy/backend-example-docker.git /app
RUN npm install
CMD FRONT_URL=http://localhost:5000 npm start
