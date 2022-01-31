# iSantePlus Docker Image

[![Build and Deploy](https://github.com/IsantePlus/docker-isanteplus-server/actions/workflows/build-and-deploy.yml/badge.svg)](https://github.com/IsantePlus/docker-isanteplus-server/actions/workflows/build-and-deploy.yml)

This repository is responsible for building the "ghcr.io/isanteplus/isanteplus" Docker image and the isanteplus mysql database image ghcr.io/isanteplus/isanteplus-mysql.

## Usage

### Build and Publish iSantePlus Image
```sh
docker-compose build --no-cache isanteplus -t ghcr.io/isanteplus/docker-isanteplus-server:latest
docker push ghcr.io/isanteplus/docker-isanteplus-server:latest
```

### Use Published Image - Docker Compose
See `docker-compose.yml` file for a working example!

Sample `docker-compose` entry:
```json
isanteplus:
    image: ghcr.io/isanteplus/docker-isanteplus-server:latest
    container_name: isanteplus
    hostname: isanteplus
    ports:
      - "8080:8080"
    healthcheck:
      test: "exit 0"
    volumes:
      - /openmrs/data
    env_file:
      - .env
```

Sample `.env` file:
```env
OMRS_JAVA_MEMORY_OPTS=-Xmx2048m -Xms1024m -XX:NewSize=128m
OMRS_CONFIG_CONNECTION_SERVER=
OMRS_CONFIG_CREATE_DATABASE_USER=false
OMRS_CONFIG_CREATE_TABLES=true
OMRS_CONFIG_ADD_DEMO_DATA=false
OMRS_CONFIG_CONNECTION_URL=
OMRS_CONFIG_HAS_CURRENT_OPENMRS_DATABASE=true
OMRS_JAVA_SERVER_OPTS=-Dfile.encoding=UTF-8 -server -Djava.security.egd=file:/dev/./urandom -Djava.awt.headless=true -Djava.awt.headlesslib=true
OMRS_CONFIG_CONNECTION_USERNAME=
OMRS_CONFIG_CONNECTION_PASSWORD=
```
