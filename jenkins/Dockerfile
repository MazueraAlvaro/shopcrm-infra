FROM jenkins/jenkins:lts

USER root

RUN apt-get update -y

RUN apt-get install ca-certificates curl gnupg lsb-release -y

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null

RUN apt-get update -y

RUN apt-get install docker-ce-cli docker-compose-plugin -y

ARG DOCKER_GID

RUN groupadd -g ${DOCKER_GID} docker

RUN usermod -aG docker jenkins

USER jenkins

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

ENV CASC_JENKINS_CONFIG /usr/local/jenkins_home/casc.yml

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

COPY casc.yml /usr/local/jenkins_home/casc.yml
