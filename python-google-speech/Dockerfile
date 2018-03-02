FROM alpine:3.7

RUN apk add --no-cache python3 \
    && python3 -m ensurepip \
    && rm -r /usr/lib/python*/ensurepip \
    && pip3 install --upgrade pip setuptools \
    && if [ ! -e /usr/bin/pip ]; then ln -s pip3 /usr/bin/pip ; fi \
    && if [[ ! -e /usr/bin/python ]]; then ln -sf /usr/bin/python3 /usr/bin/python; fi \
    && rm -r /root/.cache \
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
    && pip install numpy \
    && pip install pandas \
    && pip install scipy \
    && pip install scikit-learn \
    && pip install bcrypt \
    && pip install grpcio \
    && find /usr/lib/python3.*/ -name 'tests' -exec rm -r '{}' + \
    && rm /usr/include/xlocale.h \
    && rm -r /root/.cache \
    && apk del .build-dependencies \
    && rm -rf /var/cache/apk/*
