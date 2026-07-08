# Docker Dev Container Cheat Sheet

## Start a fresh container

Use this after rebuilding the image or after deleting the old container.

```bash
docker run -it \
  --name ubuntu-dev \
  -p 8000:8000 \
  -v ~/Workspace:/workspace \
  -v gh-config-personal:/root/.config/gh \
  -v claude-personal:/root/.claude \
  ubuntu-dev
```

---

## Resume the existing container

```bash
docker start -ai ubuntu-dev
```

---

## Stop the container

From inside the container:

```bash
exit
```

---

## Rebuild after changing the Dockerfile or for the first time

### 1. Rebuild the image/Build the image

```bash
docker build -t ubuntu-dev .
```

### 2. Remove the old container (Not needed if running for the first time)

```bash
docker rm -f ubuntu-dev
```

### 3. Start a new container

```bash
docker run -it \
  --name ubuntu-dev \
  -p 8000:8000 \
  -v ~/Workspace:/workspace \
  -v gh-config-personal:/root/.config/gh \
  -v claude-personal:/root/.claude \
  ubuntu-dev
```

---

## Optional: Remove the container

```bash
docker rm -f ubuntu-dev
```

This removes **only the container**.

Your Docker volumes remain intact:

- `gh-config-personal`
- `claude-personal`

so your GitHub and Claude logins are preserved.

---

## Useful commands

List images:

```bash
docker images
```

List containers (including stopped):

```bash
docker ps -a
```

List volumes:

```bash
docker volume ls
```

Prune old stopped containers:

```bash
docker container prune
```