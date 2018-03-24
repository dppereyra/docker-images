FROM dppereyra/python-speech

RUN apk update \
    && apk add --no-cache --virtual=.build-dependencies \
        g++ \
        gfortran \
        musl-dev \
        python3-dev \
        build-base \
        linux-headers \
        py3-cffi \
        py3-cryptography \
        libffi-dev \
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
