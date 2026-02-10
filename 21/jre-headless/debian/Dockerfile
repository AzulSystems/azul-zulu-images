FROM debian:13-slim
ARG REPO_HOST=repos.azul.com

ENV LANG='C.UTF-8'
RUN set -eux && \
    apt-get update && \
    apt-get install -y --no-install-recommends gnupg ca-certificates curl && \
    GNUPGHOME="$(mktemp -d)" && \
    export GNUPGHOME && \
    curl -fsSL https://repos.azul.com/azul-repo.key | gpg --batch --import && \
    gpg --batch --export --armor '27BC 0C8C B3D8 1623 F59B  DADC B199 8361 219B D9C9' > /usr/share/keyrings/azul.pgp.asc && \
    gpgconf --kill all && \
    rm -rf "$GNUPGHOME" && \
    echo "deb [signed-by=/usr/share/keyrings/azul.pgp.asc] https://$REPO_HOST/zulu/deb stable main" | tee /etc/apt/sources.list.d/zulu.list && \
    printf 'Package: zulu21-*\nPin: version 21.0.10-3\nPin-Priority: 1001\n' > /etc/apt/preferences && \
    apt-get update && \
    apt-get -y --no-install-recommends install zulu21-jre-headless && \
    apt-get -y purge --auto-remove gnupg curl && \
    apt-get dist-clean && \
    java -version
    
ENV JAVA_HOME=/usr/lib/jvm/zulu21

