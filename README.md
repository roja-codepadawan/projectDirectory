# projectDirectory

Create a basic project Directory

# 1. Create a repository

Clone the repository from GitHub.com to create a local copy on your computer and sync.

# 2. Dockerize an app

```
FROM python:3.10-slim
WORKDIR /code
COPY ./requirements.txt ./
RUN pip install --no-cache-dir --upgrade -r requirements.txt
COPY ./src ./src
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8080", "--reload"]
```

Use `Dockerfile` and the code in scr directory

(Use slim or alpine for smaller versions)

```
docker build -t fastapi-image .
docker run --name fastapi-container -p 8080:8080 fastapi-image
docker run -d --name fastapi-container -p 8080:8080 fastapi-image
```

# 3. Immediate file changes (volumes)

```
docker stop fastapi-container
docker ps -a
docker rm fastapi-container docker run -d --name 

fastapi-container -p 8080:8080 -v $(pwd):/code fastapi-image
```


cookbook:
https://youtu.be/0jzjz4MZ4ZU
https://github.com/patrickloeber/python-docker-tutorial
