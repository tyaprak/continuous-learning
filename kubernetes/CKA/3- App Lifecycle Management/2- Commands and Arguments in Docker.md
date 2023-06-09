````Dockerfile
FROM ubuntu:22.04

RUN sudo apt update -y && sudo apt upgrade -y

RUN or CMD ["sleep","5"] 
or 
ENTRYPOINT "sleep"
```

> docker build -t ubuntu-sleeper -f Dockerfile .

> docker run --name ubuntu-sleeper ubuntu-sleeper 10