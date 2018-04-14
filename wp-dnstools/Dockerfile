FROM wordpress:4.9-php7.2-fpm

RUN     chmod o+r /etc/resolv.conf \
        && apt-get update \
        && apt-get install -y --no-install-recommends \
            dnsutils \
            iputils-ping \
            iputils-tracepath \
            iputils-clockdiff \
            iputils-arping \
            mtr \
            nano \
        && rm -rf /var/lib/apt/lists/* \
        && rm -rf /tmp/*
