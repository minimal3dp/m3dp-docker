# Minimal3DP Docker

## M3DP Docker Config and Notes

Install On Ubuntu Server - https://discourse.ubuntu.com/t/install-and-configure-docker-engine-on-ubuntu/26182?utm_source=pocket_mylist

- In step 3.1 it should be `sudo apt update`

- Install docker-compose `sudo apt install docker-compose`

## Docker Commands

__Command List:__

- `docker container ls` - list containers
- `docker stop <Container_ID>` - stop a container
- `docker rm <Container_ID>` - remove a stopped container
- `docker rm -f <Container_ID>` - force stop and remove a container
- `docker rmi -f <Image_name>` - remove an image
- `docker-compose up -d` - run the compose file
- `docker volume ls` - list volumes
- `docker volume rm [OPTIONS] VOLUME [VOLUME...]` - remove a volume

__Danger Commands:__

- `docker kill $(docker ps -q)` - stop all containers
- `docker rm $(docker ps -a -q)` - remove all containers
- `docker rmi $(docker images -q)` - delete all images
- `docker volume rm $(docker volume ls -q)` - delete all volumes


