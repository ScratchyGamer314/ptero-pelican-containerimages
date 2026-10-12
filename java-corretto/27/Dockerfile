FROM        amazoncorretto:27

LABEL       author="Softwarenoob" maintainer="admin@softwarenoob.com"
LABEL       org.opencontainers.image.source="https://github.com/Software-Noob/pterodactyl-images"
LABEL       org.opencontainers.image.licenses="MIT"

# Corretto 22+ is based on Amazon Linux 2023 (dnf, curl-minimal preinstalled)
RUN         dnf upgrade -y \
            && dnf install -y --setopt=install_weak_deps=False ca-certificates openssl git tar sqlite fontconfig freetype freetype-devel libstdc++ lsof tzdata iproute \
            gcc gcc-c++ automake make libtool shadow-utils glibc-langpack-en \
            && dnf clean all \
            && rm -rf /var/cache/dnf \
            && useradd -m -d /home/container container

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
