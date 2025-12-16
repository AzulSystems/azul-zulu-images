FROM rockylinux/rockylinux:10.1
ARG REPO_HOST=repos.azul.com
ENV LANG='en_US.UTF-8'

RUN set -e && \
  printf '%s\n' \
    '[zulu-openjdk]' \
    'name=zulu-openjdk - Azul Systems Inc., Zulu packages' \
    "baseurl=https://${REPO_HOST}/zulu/rpm" \
    'gpgkey=https://repos.azul.com/azul-repo.key' \
    'enabled=1' \
    'gpgcheck=1' \
    'protect=1' \
  > /etc/yum.repos.d/zulu-openjdk.repo
RUN yum -y update && \
yum -q -y install fontconfig zulu11-jre-headless-11.0.29-1 && \
yum clean all && \
rm -rf /var/cache/yum && \
rm -f /etc/yum.repos.d/zulu-openjdk.repo

ENV JAVA_HOME=/usr/lib/jvm/zulu11
