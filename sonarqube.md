## SonarQube :: Docker on Linux


Config for Linux
```
sysctl -w vm.max_map_count=524288
sysctl -w fs.file-max=131072
ulimit -n 131072
ulimit -u 8192
```

Create docker volume
```
docker volume create --name sonarqube_data
docker volume create --name sonarqube_logs
docker volume create --name sonarqube_extensions
```

Create and start container with Docker
```
docker container run -d --name sonarqube \
    -p 9000:9000 \
    -v sonarqube_data:/opt/sonarqube/data \
    -v sonarqube_extensions:/opt/sonarqube/extensions \
    -v sonarqube_logs:/opt/sonarqube/logs \
    sonarqube:8.9.7-community
```


### Reference websites
* https://hub.docker.com/_/sonarqube
* https://docs.sonarqube.org/latest/setup/install-server/
* https://github.com/up1/workshop-java-web-tdd
