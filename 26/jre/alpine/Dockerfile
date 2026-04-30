FROM alpine:3.23
ARG REPO_HOST=repos.azul.com
ENV LANG='C.UTF-8'
RUN set -eux; \
     wget -O /tmp/azul-signing.pub https://cdn.azul.com/public_keys/alpine-signing@azul.com-5d5dc44c.rsa.pub; \
     echo "6c6393d4755818a15cf055a5216cffa599f038cd508433faed2226925956509a  /tmp/azul-signing.pub" | sha256sum -c -; \
     mv /tmp/azul-signing.pub /etc/apk/keys/alpine-signing@azul.com-5d5dc44c.rsa.pub; \
     echo "https://$REPO_HOST/zulu/alpine" | tee -a /etc/apk/repositories; \
     apk add --no-cache zulu26-jre=26.0.1-r1; \
     java -version

ENV JAVA_HOME=/usr/lib/jvm/zulu26
ENV PATH=$JAVA_HOME/bin:$PATH

