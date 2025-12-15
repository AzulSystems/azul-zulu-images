FROM alpine:3.23
ARG REPO_HOST=repos.azul.com
ENV LANG=en_US.UTF-8
RUN set -e && \
    wget -P /etc/apk/keys/ https://cdn.azul.com/public_keys/alpine-signing@azul.com-5d5dc44c.rsa.pub && \
    echo "https://$REPO_HOST/zulu/alpine" | tee -a /etc/apk/repositories && \
    apk update && \
    apk add --no-cache zulu25-jdk=25.0.1-r1

ENV JAVA_HOME=/usr/lib/jvm/zulu25
