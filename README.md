# shopcrm-infra

## Jenkins
### Build jenkins image

```
docker buils -t jenkins:jcasc .
```
### Create and set permission jenkins home volume
### Run Jenkins container

```
docker run -p 8080:8080 -p 50000:50000 --env JENKINS_ADMIN_ID=admin \
--env JENKINS_ADMIN_PASSWORD=admin --env JENKINS_URL=https://localhost:8080 \
--rm -v //var/run/docker.sock:/var/run/docker.sock \
-v $(which docker):/usr/local/bin/docker -v ~/jenkins_home:/var/jenkins_home \
--name jenkins jenkins:jcasc
```
> **Note:** Please use a unix like system to run this command