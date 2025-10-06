# Clase 2 - Dockerización de Mi Aplicación

## Aplicación

**Lenguaje:** python
**Framework:** Flask
**Descripción:** API REST para obtener nombre y correo de un usuario

**Endpoints:**
- GET / - Obtener usuario
- PUT /users/id - actualizar usuario
- DELETE /users/id - borrar usuario

## Dockerfile

\`\`\`dockerfile
# Stage 1: Build
FROM python:3.6-slim-buster

WORKDIR /app

COPY requirements.txt ./

RUN pip install -r requirements.txt

COPY . .

EXPOSE 4000

CMD [ "flask", "run", "--host=0.0.0.0", "--port=4000"]

# Stage 2: Production
FROM node:18-alpine
...
\`\`\`

**Explicación:**

| Stage | Propósito |
|-------|-----------|
| Build | Instalar todas las dependencias... |
| Production | Solo runtime... |

## Build

\`\`\`bash
docker build -t tasks-api:1.0 .
\`\`\`

**Salida:**
\`\`\`
[+] Building 32.5s ...
Successfully tagged tasks-api:1.0
\`\`\`

**Tamaño final:** 145MB

## Testing

![Docker Images](screenshots/docker-images.png)
![Container Running](screenshots/docker-ps.png)
![API Response](screenshots/curl-response.png)

## Docker Hub

**URL:** https://hub.docker.com/r/miusuario/tasks-api

![Docker Hub](screenshots/dockerhub.png)

## Optimizaciones

- Multi-stage build: redujo de 320MB a 145MB
- Usuario non-root
- .dockerignore excluye node_modules
