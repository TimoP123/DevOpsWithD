# Part 1 exercises

## 1.1

```
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED              STATUS                      PORTS               NAMES
244a5a81b588        nginx               "nginx -g 'daemon ..."   56 seconds ago       Exited (0) 11 seconds ago                       quizzical_euclid
23fd882a2f2d        nginx               "nginx -g 'daemon ..."   58 seconds ago       Exited (0) 3 seconds ago                        nifty_cray
9e9c2bdcc8bf        nginx               "nginx -g 'daemon ..."   About a minute ago   Up About a minute           80/tcp              peaceful_pare
```

## 1.2

```
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE

```

## 1.3

Run a container, install curl, listen to a website address and fetch website:

```
docker run -d --rm -i --name curler ubuntu:16.04 sh -c 'apt update && apt install -y curl; while true; do read website; sleep 3; curl http://$website; done'

```

If we now attach container and give an address, the curler will fetch the website.

```
$ docker attach --sig-proxy=false curler
helsinki.fi
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   231  100   231    0     0    669      0 --:--:-- --:--:-- --:--:--   671
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>

```

## 1.4

Files to build the curler image are [Dockerfile](1.4/Dockerfile) and [script.sh](1.4/script.sh).

Build the image with command `docker build -t curler .`  
Run the image with command `docker run -it curler`

Output matches with the previous exercise.

## 1.5

Build image using [Dockerfile](1.5/Dockerfile) and command `docker build -t frontend-example .`
When the image is run with command `docker run -d -p 5000:5000 frontend-example` the application can be found with browser from address localhost:5000

## 1.6

Build image using [Dockerfile](1.6/Dockerfile) and command `docker build -t backend-example .`
Create an empty logfile: `touch logs.txt`
Run image: `docker run -d -p 8000:8000 -v $(pwd)/logs.txt:/app/logs.txt backend-example`
Open location localhost:8000 with browser.

## 1.7

Build images in backend [Dockerfile](1.7/backend/Dockerfile) and frontend [Dockerfile](1.7/frontend/Dockerfile) folders with commands `docker build -t frontend .` and `docker build -t backend .` respectively.
Create an empty logfile: `touch logs.txt`  
Run backend: `docker run -d -p 8000:8000 -v $(pwd)/logs.txt:/app/logs.txt backend`  
Run frontend: `docker run -d -p 5000:5000 frontend`  
Open location localhost:5000 with browser.

## 1.9

Image can be built from [Dockerfile](1.9/Dockerfile) with command `docker build -t golang_dev_env .` or pulled from [Docker Hub](https://hub.docker.com/r/timop/golang_dev_env).

Run image with command `docker run -it -p 8000:8000 timop/golang_dev_env`
