## Docker: Debian - NGINX

**Dockerfile** of [Debian](https://www.debian.org/) - [NGINX](https://www.nginx.com/) [Docker](https://www.docker.com/) image.

Based on the official NGINX [Dockerfile](https://github.com/nginxinc/docker-nginx).

### Base Docker Image

- [debian:jessie](https://hub.docker.com/_/debian/)

### Development

Build an image from Dockerfile with the tag `debian/nginx`:

    $ docker build -t="debian/nginx" -f ./Dockerfile .

### Usage

List running containers:

    $ docker ps [-a] # Use -a to lists all containers.

Run docker image:

    $ docker run -d -p 80:80 <image_name|container_id>
    # e.g: docker run -d -p 80:80 debian/nginx

View docker logs:

    $ docker logs <container_name>
    # e.g: docker logs romantic_ride

Welcome page: after a few seconds, open http://<host> (e.g: 192.168.99.100) to see the welcome page.

Access Docker container:

    $ docker exec -it romantic_ride bash
