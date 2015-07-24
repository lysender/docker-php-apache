# Generic PHP Apache Docker container

Generic PHP Apache docker container built on CentOs 7.

Note: This repo just serves as a base image for building PHP/Apache based containers. You can extend this by using the existing image (the result of this Docker file repo) at https://registry.hub.docker.com/u/lysender/php-apache/ by Docker Hub. 

## Requirements

You must have at least Docker 1.6.2 where this Dockerfile is tested. It is also nice to have a fast internet connection or best if you do this on a VPS or some cloud hosting account.

## Installation

For testing purposes, like a hello workd application (in our case, a phpinfo() output), we can build the image this way.

Note: I prefer to create images and containers as a regular user. You may choose to run it as root.

    # Clone this repo
    git clone git@github.com:lysender/docker-php-apache.git
    cd docker-php-apache
    
    # Build image, you can use any tag name
    docker build --rm -t lysender/php-apache .
    
    # Create and run a container on poart 8080
    docker run --name sample-php -d -p 8080:80 lysender/php-apache

The first part (building the image) will take some time to complete. Fast connection helps.

After building, we create a container based on the newly created image, configure it to run as a daemon `-d`, map the exposed port to `8080` where it maps to the containers port `80`. 

You can then test this by visiting http://127.0.0.1:8080 or the IP address of your VPS like http://your-vps-ip:8080.

The output is a `phpinfo()` page based on our sample `index.php` file. 

## Troubleshooting

Site does not load? Try checking if the container is still running.

    docker ps

It should show the currently running containers. It `sample-php` container is not listed, or has exited for some reasons, then there are issues when the image or container.

TODO: Add more troubleshooting information.
