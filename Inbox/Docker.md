

06-07-2025 10:56

Status: #in_progress

Tags:

# Docker




## Dockerfile

- **Purpose:** Defines how to **build a Docker image**.
- **Contains:** Instructions to set up the environment (e.g., base image, installing packages, copying files).
- **Result:** When you run `docker build`, it creates a **Docker image**.

Think of it as a recipe for baking a cake.

- [[Docker#build|build]]
- [[Docker#volumes|Volumes]]

### build

for a specific *Dockerfile*
``` bash
docker build -t my-image-name -f path/to/Dockerfile path/to/context
```
- -t gives name (tag) to the image (my-nb-image)
- -f specifies the *Dockerfile* to use
- path/to/context is the folder where docker looks to use *COPY*, *ADD* etc. commands int eh *Dockerfile*
for example if the Dockerfile contains
``` Dockerfile
COPY requirements.txt /app/
```
Docker will look for `requirements.txt` **in the context directory**

[[Docker#volumes|Volumes]]

### volumes
``` Dockerfile
volumes:
  - ./data:/app/data # use data folder in current directory
  - /absolute/path/on/host:/app/data

```
The **left side is a path on the host machine**

``` Dockerfile
volumes:
  - myvolume:/app/data
```
The **left side is not a path**, just a name
Docker uses a *Docker-managed volume*. 
Data is stored in:
- Linux: `/var/lib/docker/volumes/myvolume/_data`

``` bash
docker volume ls                   # Lists named volumes
docker volume inspect myvolume     # Shows mount path and metadata
```
## docker-compose

docker-compose.yml

- **Purpose:** Defines how to **run one or more containers** based on Docker images.
- **Contains:** Configuration like environment variables, volumes, ports, networks, dependencies between services, etc.
- **Result:** When you run `docker-compose up`, it **builds (if needed) and starts containers**.

Think of it as a party planner deciding how many cakes to bake and where to put them on the table

[[Docker#up|docker compose up]]

### up
``` bash
docker compose up -d # runs the containers in the background
```

`docker-compose.yml` can reference a `Dockerfile` using the `build:` directive

``` yaml
services:
  web:
    build: .
    ports:
      - "8080:80"

```
This means: "build an image using the Dockerfile in this directory, then run a container from it and expose port 80 as 8080 on the host."
## handle images

### display images
``` bash
docker images
docker images --format "{{.Repository}}:{{.Tag}}" 
docker image prune # remove unused images
```
### remove image
``` bash
docker rmi abcdef123456
docker rmi yourproject_web:latest # by tag
```
## handle containers
### display  containers
``` bash
docker ps # display running containers
docker ps -a # display all 
sudo docker ps -a --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Image}}"
```
### remove container
``` bash
docker rm <container_name_or_id>
docker rmi -f <image_id_or_name>
```
### inspect
``` bash
docker inspect <containerID>
docker inspect <containerID> --format '{{.Config.Image}}'
```
### logs
``` bash
docker logs web
```
### interactive shall
``` bash
docker exec -it <container_name> /bin/bash
```

### stop container
``` bash
docker compose stop # stops containers
```
### stop and remove containers
``` bash
docker compose down
docker compose down --volumes # This will delete named volumes!
```
All containers started by the current `docker-compose.yml` are **stopped** and then **removed**. *Network* is also deleted.


## example
docker-compose.yml
``` yaml
services:
  os:
    image: opensearchproject/opensearch:latest
    environment:
      - discovery.type=single-node
      - bootstrap.memory_lock=true
      - "OPENSEARCH_JAVA_OPTS=-Xms512m -Xmx512m"
      - DISABLE_SECURITY_PLUGIN=true
      - DISABLE_INSTALL_DEMO_CONFIG=true
      - "OPENSEARCH_INITIAL_ADMIN_PASSWORD=Argmax123!"
    ulimits:
      memlock:
        soft: -1
        hard: -1
      nofile:
        soft: 65536
        hard: 65536
    volumes:
      - opensearch-data:/usr/share/opensearch/data
    ports:
      - "9200:9200"
      - "9600:9600"
    networks:
      - argmax
    healthcheck:
      test: ["CMD-SHELL", "curl -s -f http://localhost:9200/_cluster/health || exit 1"]
      interval: 10s
      timeout: 5s
      retries: 3
      start_period: 20s
  web:
    build:
      context: web
      dockerfile: Dockerfile
    environment:
      - FLASK_APP=app.py
      - FLASK_ENV=development
      - FLASK_DEBUG=1
      - OPENSEARCH_URL=http://os:9200
    ports:
      - "8080:8080"
    volumes:
      - ./web/src:/app/web
    networks:
      - argmax
    depends_on:
      os:
        condition: service_healthy
  nb:
    build:
      context: nb
      dockerfile: Dockerfile
    environment:
      - OPENSEARCH_URL=http://os:9200
    ports:
      - "8890:8888"
    volumes:
      - ./nb/src:/usr/src/app
    networks:
      - argmax
    depends_on:
      os:
        condition: service_healthy
volumes:
  opensearch-data:
networks:
  argmax:
    driver: bridge
```



## Example
docker-copmpose.yml


## My Questions


## References

