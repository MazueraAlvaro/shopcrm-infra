FROM jenkins/jenkins:lts

ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

ENV CASC_JENKINS_CONFIG /usr/local/jenkins_home/casc.yml

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt

COPY casc.yml /usr/local/jenkins_home/casc.yml