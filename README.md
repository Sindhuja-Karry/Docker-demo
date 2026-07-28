# Docker-demo

A minimal project for learning the basics of **Docker** — writing a `Dockerfile`, building an image, and running it as a container.

##  What's in this repo

"Dockerfile"  Defines how to build the image 

"app.py"   A single-line Python script the container runs on startup 

##  How the Dockerfile works, step by step

```dockerfile
FROM ubuntu:latest
WORKDIR /app
COPY . /app
RUN apt-get update && apt-get install -y python3 python3-pip
ENV NAME World
CMD ["python3", "app.py"]
```

1. **`FROM ubuntu:latest`** — starts from a plain Ubuntu base image (no Python pre-installed).
2. **`WORKDIR /app`** — sets `/app` as the working directory inside the image; later commands run relative to this path.
3. **`COPY . /app`** — copies everything from this repo into `/app` in the image, including `app.py`.
4. **`RUN apt-get update && apt-get install -y python3 python3-pip`** — installs Python 3 and pip inside the image, since the base Ubuntu image doesn't include them.
5. **`ENV NAME World`** — sets an environment variable available inside the container (not currently used by `app.py`, but demonstrates the `ENV` instruction).
6. **`CMD ["python3", "app.py"]`** — the default command run when the container starts: executes `app.py`, which prints `hello world`.

## How to run

# Build the image
docker build -t docker-demo .

# Run the container
docker run docker-demo

## Status

🚧 Learning project — first pass at Docker fundamentals (base images, `WORKDIR`, `COPY`, `RUN`, `CMD`) before moving on to multi-stage builds and web apps.
