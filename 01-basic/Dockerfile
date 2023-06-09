FROM jenkins/jenkins:2.409-alpine-jdk17
USER root
RUN apk update && apk add --no-cache docker-cli
USER jenkins
# copy the jenkins plugins file
COPY --chown=jenkins:jenkins plugins.txt /usr/share/jenkins/ref/plugins.txt
# install plugins from the plugins file
RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt
# turn off wizard and allow local checkout
ENV JAVA_OPTS "-Dhudson.plugins.git.GitSCM.ALLOW_LOCAL_CHECKOUT=true -Djenkins.install.runSetupWizard=false"
