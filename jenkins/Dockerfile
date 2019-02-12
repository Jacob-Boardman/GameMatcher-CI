#Start off with a Jenkins base images
FROM jenkins/jenkins:latest

#installing the plugins we need to using in-built install-plugins.sh script
RUN /usr/local/bin/install-plugins.sh git matrix-auth workflow-aggregator docker-workflow blueocean credentials-binding

#setting up enviroment varibles for the admin user
ENV JENKINS_USER admin
ENV JENKINS_PASS admin

#skip the inital setup wziard
ENV JAVA_OPTS -Djenkins.install.runSetupWizard=false

#start-up scripts to set number of executors and creating the admin user and plugins
COPY init.groovy /usr/share/jenkins/ref/init.groovy.d/init.groovy
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins.txt
