# CentOS notes


## Install docker on CentOS

Found guidelines [here](https://nixcp.com/docker-command-not-found/).

1. To install first install dependencies:

```bash
sudo yum install yum-utils device-mapper-persistent-data lvm2
```

2. Add Docker repo:
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

3. Install Docker:
```bash
yum install docker-ce
```

4. Start docker:
```bash
sudo systemctl start docker
```
## Change default Docker storage location
1. Check the current path (in case of restricted space)
```console
$ sudo docker info -f '{{ .DockerRootDir }}'
/var/lib/docker
```
2. Create a new target path (example):
```bash
mkdir -p /disk2/pavfrang/docker
```
3. Configure docker daemon. Edit the file (e.g. via nano): `/etc/docker/daemon.json` by adding the following content:
```json
{ 
   "data-root": "/disk2/pavfrang/docker"
}
```
4. Restart the docker service and check if the current location is the desired one:
```console
$ sudo systemctl restart docker
$ sudo docker info -f '{{ .DockerRootDir }}'
/disk2/pavfrang/docker
```
### Install CARLA

To run CARLA via docker use the guide [here](https://carla.readthedocs.io/en/latest/build_docker/).

Pull CARLA image:
```bash
sudo docker pull carlasim/carla:latest
```

