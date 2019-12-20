# Microservice - AWS - Demo - Project - Jenkins

This page explains how I run Jenkins as part of doing CI/CD for my microservice-aws-demo project.

I run Jenkins on a Docker container using the following docker command (as shown from Jenkins Documentation):

```bash
docker run \
  -u root \
  --rm \
  -d \
  -p 7000:8080 \
  -v $HOME/dev/jenkins:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME":/home \
  jenkinsci/blueocean
```

- running as root user
- removing the container when shutdown Jenkins
- running as a daemon process in the background
- mapping Jenkins default container port of 8080 to my host port of 7000*
- mapping /var/jenkins_home dir to somewhere in my local filesystem ($HOME/dev/jenkins)
- bind the docker.sock from the Jenkins Docker container to my host's Docker so that the Jenkins Container can spawn docker containers as 'build containers' using my host's Docker
- running the jenkinsci/blueocean docker image (this has Blue Ocean plugin pre-installed)


*i chose 7000 as I simply didn't want to use the default port of 8080 (i reserve that for my java spring boot microservice apps)
