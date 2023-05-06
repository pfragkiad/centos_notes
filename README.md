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

4. Run docker:
```bash
systemctl start docker
```


