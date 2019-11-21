# Docker

## Docker - The era of containerized applications 

### Virtualization

- Virtual Machines
- VM ware | Virtual Box | Hyper Visior

### Vagrant 

- A Virtual Machine manager
- One VM per projects approach
- headless VMs | faster than normal | built on top of VirtualBox
- all of the dev environment is configured with vagrant file.
- vagrant up - is all i need to get a project up and running.
- works on the idea of base box | then build on top of it.

### Containerization

- Containers
- one process per container approach
- Docker 
- difference between Virtual Machine and docker
- use case for docker - experiment, development, production, testing, maintainance

### Docker 

- [Learn Docker in 12 Minutes](https://www.youtube.com/watch?v=YFl2mCHdv24)
- Installation
- `docker images`
- `docker pull` images
- `docker run` -it | -d | -e 
- docker start | stop
- `Dockerfiles`
- `docker build` - using Dockerfile to build containers
- docker commit - saving container state as a image
- binding volumes with container - to reflect changes instantly

### Docker Composer 

- [Learn docker-composer in 12 Minutes](https://www.youtube.com/watch?v=Qw9zlE3t8Ko)
- containers linking 
	- `--link` => depreciated
	- common network mode => tedious
	- `docker-composer` => A newer way to interlink containers
- spin out multiple containers - quickly and easily
- creates a network automatically, then containers can be addressed by their names
- port exposure - forwarding requests from host machine to containers via exposed ports
- persistent storage 
	- volume mapping - host to container => managed by docker
	- volume container - as a data access point container for all other containers
- YML file => specifying services for each container, their exposed ports
- docker-composer up => single command application up and down for multi container applications

## Conclusion

### Single container based application
- make a directory that holds your source code
- make a Dockerfile in it, build a docker image
- spin up a container with -p for correct port forward and -v for shared directory mount

### Multi container application
- docker-composer to manage all containers
- write YML carefully and you are good to go.

## More - What is a Container Orchestrator

If one container crash, there is no automatic restart. If one container restart you have to restart all container to resync link (other container keep the old ip). you have to use only one host, scale is hard, 
