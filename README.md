Multiple docker Node.js images from one context root and one master set of dependencies.

Without docker-compose:

```bash
# build images
docker build --tag awesome_app1  --file Dockerfile.app1 .
docker build --tag awesome_app2  --file Dockerfile.app2 .

# run containers
docker run --detach --name awesome_app1 --publish 8081:8080 awesome_app1:latest
docker run --detach --name awesome_app2 --publish 8082:8080 awesome_app2:latest

# try them
curl -s http://localhost:8081
Hello world... I am app1

curl -s http://localhost:8082
Hello world... I am app2

# stop containers
docker stop awesome_app1 awesome_app2
docker rm awesome_app1 awesome_app2

# remove image
docker rmi awesome_app1 awesome_app2
```

With docker-compose:
```bash
# create and start containers
docker-compose up -d

# try them
curl -s http://localhost:8081
Hello world... I am app1

curl -s http://localhost:8082
Hello world... I am app2

# stop containers
docker-compose stop
docker-compose rm -f
```