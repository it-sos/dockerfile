FROM python:3.10.5-alpine3.16
ENV DOCKERIZE_VERSION v0.6.1

WORKDIR /opt

# install mysqlclient
RUN apk update \
    && apk add --virtual build-deps gcc musl-dev \
    && apk add --no-cache mariadb-dev\
    && apk del build-deps

RUN pip3 install virtualenv \
    && cd /opt \
    && ln -fs /usr/local/python3/bin/virtualenv /usr/bin/virtualenv \
    && virtualenv venv4cmdb --python=python3 \
    && cd /opt \
    #dockerize
    && wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-alpine-linux-amd64-$DOCKERIZE_VERSION.tar.gz
