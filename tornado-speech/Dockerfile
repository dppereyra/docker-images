# ffmpeg - http://ffmpeg.org/download.html
#

FROM dppereyra/python-speech

RUN apk update \
    && apk add --no-cache --virtual=.build-dependencies \
        g++ \
        gfortran \
        file \
        binutils \
        musl-dev \
        python3-dev \
        build-base \
    && update-ca-certificates \
    && ln -s locale.h /usr/include/xlocale.h \
    && pip install \
        tornado \
        wsaccel \
    && find /usr/lib/python3.*/ -name 'tests' -exec rm -r '{}' + \
    && rm /usr/include/xlocale.h \
    && rm -r /root/.cache \
    && apk del .build-dependencies \
    && rm -rf /var/cache/apk/* \
    && rm -rf /tmp/*
