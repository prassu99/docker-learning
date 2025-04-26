# Docker-Learning
# 🐳 Day 1: Getting Started with Docker

## ✅ What I Did Today
- Installed Docker on my local machine.
- Ran my **first Docker container** using `hello-world`.
- Learned basic Docker commands.
- Understood the difference between **images** and **containers**.
- Created this GitHub repo to document my Docker learning journey.

---

## 🔧 Commands I Used

```shell
#Check Docker version
docker --version
```
<img width="302" alt="image" src="https://github.com/user-attachments/assets/48bcdb82-4e54-49ec-9cdb-af5000aab415" />
<br>

```shell
#Run Hello world image
docker run hello-world
```
<img width="708" alt="image" src="https://github.com/user-attachments/assets/6d413a1f-3b3f-4496-b69a-3ae283930cc8" />

<br>

```shell
#See running containers
docker ps
```

```shell
#See all containers
docker ps -a
```

```shell
#See images
docker images
```

```shell
#Stop a docker container where c73cd6ffde7c is a container Id
docker stop c73cd6ffde7c
```


```shell
#Remove a docker container where c73cd6ffde7c is a container Id
docker rm c73cd6ffde7c
```


```shell
#Remove a docker image
docker rmi hello-world
```

```shell
#Removes all unused containers, networks, and dangling images.
docker system prune
```

# 🐳 Day 2: My First Dockerfile (Python App)

## ✅ What I Did Today
- Created a simple Python script.
- Wrote my first custom `Dockerfile`.
- Built a Docker image and ran it locally.
- (Optional) Pushed the image to DockerHub.
- Learned about how Dockerfiles define the build steps.

---

## 🧠 Docker Concepts I Practiced

| Dockerfile Instruction | What It Does |
|------------------------|--------------|
| `FROM` | Defines the base image (Python 3.11) |
| `WORKDIR` | Sets the working directory inside the container |
| `COPY` | Copies files from my machine into the container |
| `CMD` | Defines the command that runs by default in the container |

---
## 📝 Python Script (`app.py`)

```python
print("Hello from my first Docker container!")
```

```Dockerfile
#Docker file used
FROM python:3.11-slim
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

```shell
#Build the docker image
docker build -t hello-python .
```

```shell
#Run the Container
docker run hello-python
#Output -
Hello from my first Docker container!
```


```shell
#Docker login to hub and tag the image and push the image to hub
docker login
docker tag hello-python prasannamarru/hello-python
docker push prasannamarru/hello-python
```

```shell
#Run it from anywhere
docker run prasannamarru/hello-python
```
<img width="654" alt="image" src="https://github.com/user-attachments/assets/b816710b-2272-491c-b92b-79585ed05530" />

# 🐳 Day 3: Running PostgreSQL + Adminer with Docker Compose

## ✅ What I Did Today
- Learned about **Docker Compose** to run multiple services together.
- Set up **PostgreSQL** (database) + **Adminer** (web UI) using a single `docker-compose.yml` file.
- Connected to PostgreSQL using the Adminer web interface.
- Practiced creating tables, inserting data, and running simple SQL queries.

---

## 📚 What is Docker Compose?
- Docker Compose allows you to **define and run multi-container applications** easily.
- You describe services, networks, and volumes in a simple `docker-compose.yml` file.
- One command (`docker-compose up`) can start everything together!

---


## ⚙️ docker-compose.yml Used

```yaml
version: '3.8'

services:
  db:
    image: postgres:14
    container_name: postgres-db
    restart: always
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: password123
      POSTGRES_DB: testdb
    ports:
      - "5432:5432"

  adminer:
    image: adminer
    container_name: adminer-ui
    restart: always
    ports:
      - "8080:8080"

```

▶️ How to Run
```shell
docker-compose up -d
```

# Tested the container locally-

