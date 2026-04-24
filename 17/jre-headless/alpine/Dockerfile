FROM alpine:3.23
ARG REPO_HOST=repos.azul.com
ENV LANG='C.UTF-8'
RUN set -eux && \
    wget -P /etc/apk/keys/ https://cdn.azul.com/public_keys/alpine-signing@azul.com-5d5dc44c.rsa.pub && \
    echo "https://$REPO_HOST/zulu/alpine" | tee -a /etc/apk/repositories && \
    apk update && \
    apk add --no-cache zulu17-jre-headless=17.0.19-r3 && \
    java -version

ENV JAVA_HOME=/usr/lib/jvm/zulu17
ENV PATH=$JAVA_HOME/bin:$PATH

