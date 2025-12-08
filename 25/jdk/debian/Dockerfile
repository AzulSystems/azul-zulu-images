FROM debian:13.1
ARG REPO_HOST=repos.azul.com

ENV LANG='en_US.UTF-8'
RUN apt update && \
    apt install -y gnupg ca-certificates curl && \
    curl -s https://repos.azul.com/azul-repo.key | gpg --dearmor -o /usr/share/keyrings/azul.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/azul.gpg] https://$REPO_HOST/zulu/deb stable main" | tee /etc/apt/sources.list.d/zulu.list && \
    echo "Package: zulu25-*\nPin: version 25.0.1-1\nPin-Priority: 1001" > /etc/apt/preferences && \
    apt update && \
    apt-get -qq -y --no-install-recommends install zulu25-jdk && \
    apt-get -qq -y purge --auto-remove gnupg curl && \
    apt-get -qq -y autoremove && \
    apt-get -qq clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -f /etc/apt/sources.list.d/zulu.list

ENV JAVA_HOME=/usr/lib/jvm/zulu25
