FROM golang:1.4.2

WORKDIR /mydir
EXPOSE 8000

RUN apt-get update && apt-get install -y curl git
RUN curl https://glide.sh/get | sh
RUN go get github.com/codegangsta/gin

CMD ["/bin/bash"]
