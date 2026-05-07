FROM almalinux:10
ARG REPO_HOST=repos.azul.com
ENV LANG='C.UTF-8'
RUN  set -eux; \
     dnf install -y --setopt=install_weak_deps=False gnupg2; \
     curl -fsSL https://repos.azul.com/azul-repo.key -o /tmp/azul-repo.key; \
     GNUPGHOME="$(mktemp -d)"; export GNUPGHOME; \
     gpg --batch --import /tmp/azul-repo.key; \
     gpg --batch --list-keys --fingerprint --with-colons \
       | awk -F: '$1 == "fpr" { print $10 }' \
       | grep -Fxq '27BC0C8CB3D81623F59BDADCB1998361219BD9C9'; \
     gpgconf --kill all; rm -rf "$GNUPGHOME"; \
     rpm --import /tmp/azul-repo.key; \
     rm /tmp/azul-repo.key; \
     printf '%s\n' \
       '[zulu-openjdk]' \
       'name=zulu-openjdk - Azul Systems Inc., Zulu packages' \
       "baseurl=https://$REPO_HOST/zulu/rpm" \
       'enabled=1' \
       'gpgcheck=1' \
       'gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-azul' \
       > /etc/yum.repos.d/zulu-openjdk.repo; \
     curl -fsSL https://repos.azul.com/azul-repo.key -o /etc/pki/rpm-gpg/RPM-GPG-KEY-azul; \
     dnf install -y --setopt=install_weak_deps=False fontconfig \
       zulu21-jre-headless-21.0.11-3; \
     dnf remove -y gnupg2; \
     dnf clean all; rm -rf /var/cache/dnf; \
     java -version

ENV  JAVA_HOME=/usr/lib/jvm/zulu21
ENV  PATH=$JAVA_HOME/bin:$PATH

