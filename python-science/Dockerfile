FROM dppereyra/ffmpeg-audio

RUN mkdir -p /applib
COPY stack-fix.c /applib/

RUN apk add --no-cache python3 \
    && python3 -m ensurepip \
    && rm -r /usr/lib/python*/ensurepip \
    && pip3 install --upgrade pip setuptools \
    && if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi \
    && if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi \
    && rm -r /root/.cache \
    && apk update \
    && apk add --no-cache libstdc++ lapack-dev \
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
        ca-certificates \
    && update-ca-certificates \
    && ln -s locale.h /usr/include/xlocale.h \
    && gcc -shared -fPIC /applib/stack-fix.c -o /applib/stack-fix.so \
    && pip install numpy \
    && pip install \
        pandas \
        scipy \
        scikit-learn \
        bcrypt \
    && find /usr/lib/python3.*/ -name 'tests' -exec rm -r '{}' + \
    && rm /usr/include/xlocale.h \
    && rm -r /root/.cache \
    && apk del .build-dependencies \
    && rm -rf /var/cache/apk/* \
    && rm -rf /tmp/*
