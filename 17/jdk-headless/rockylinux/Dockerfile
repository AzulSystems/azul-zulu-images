FROM rockylinux/rockylinux:10.0
ARG REPO_HOST=repos.azul.com
ENV LANG='en_US.UTF-8'

RUN set -e && tee /etc/yum.repos.d/zulu-openjdk.repo > /dev/null <<EOF
[zulu-openjdk]
name=zulu-openjdk - Azul Systems Inc., Zulu packages
baseurl=https://$REPO_HOST/zulu/rpm
gpgkey=https://repos.azul.com/azul-repo.key
enabled=1
gpgcheck=1
protect=1
EOF
RUN yum -y update && \
yum -q -y install zulu17-jdk-headless-17.0.17-1 && \
yum clean all && \
rm -rf /var/cache/yum && \
rm -f /etc/yum.repos.d/zulu-openjdk.repo

ENV JAVA_HOME=/usr/lib/jvm/zulu17
