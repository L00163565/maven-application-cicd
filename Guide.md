Steps

1. Run jenkins in a docker container:

$  docker run -d -p 8080:8080 --name jenkins-instance-1 jenkins/jenkins:latest
$ docker exec -it 2aea26627ae1 bin/bash

## check jenkins verion in docker container
$ java -jar /usr/share/jenkins/jenkins.war --version
