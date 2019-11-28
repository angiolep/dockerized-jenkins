FROM jenkins/ssh-slave:jdk11

# WARN The base image is deriving from Debian SID (unstable!)
#      We has to explicitely fallback to Debian buster (see below)
#

RUN apt-get update \
 && apt-get -y --no-install-recommends install \
        apt-transport-https \
        ca-certificates \
        curl \
        gnupg-agent \
        software-properties-common \
 && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
 && apt-key fingerprint 0EBFCD88 \
 && add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian buster stable" \
 && apt-get update \
 && apt-get -y --no-install-recommends install \
        docker-ce \
        docker-ce-cli \
        containerd.io \
 && usermod -aG root jenkins \
 && rm -rf /var/lib/apt/lists/*


