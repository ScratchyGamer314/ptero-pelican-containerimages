FROM        python:3.10-slim

LABEL       author="Auroa Online" maintainer="hello@auroa.cloud"
LABEL       org.opencontainers.image.source="https://github.com/medaria/ptero-pelican-containerimages"
LABEL       org.opencontainers.image.licenses="MIT"

RUN         apt-get update \
            && apt-get -y install --no-install-recommends git gcc g++ ca-certificates dnsutils curl iproute2 ffmpeg procps locales \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/* \
            && useradd -m -d /home/container container \
            && locale-gen en_US.UTF-8

ENV         LC_ALL=en_US.UTF-8
ENV         LANG=en_US.UTF-8
ENV         LANGUAGE=en_US.UTF-8

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
