FROM jenkins/jenkins:alpine

ADD .ssh /var/jenkins_home/.ssh

USER root
RUN chown -R jenkins:jenkins /var/jenkins_home/.ssh \
 && chmod 600 /var/jenkins_home/.ssh/id_rsa*

USER jenkins

