FROM kuwork/alpine:3.10.1-aarch64

ARG BUILD_DATE
ARG VCS_REF
ENV MYSQL_ROOT_PASSWORD raspberry123
ENV MYSQL_CHARSET utf8
ENV MYSQL_COLLATION utf8_general_ci
ENV MYSQL_USER pi
ENV MYSQL_PASSWORD raspberry
ENV MYSQL_DATABASE db

LABEL maintainer="kuwork <kuwork@126.com>" \
    architecture="arm64v8/aarch64" \
    mariadb-version="10.3.17" \
    alpine-version="3.10.1" \
    build="19-Aug-2019" \
    org.opencontainers.image.title="alpine-mariadb" \
    org.opencontainers.image.description="MariaDB Docker image running on Alpine Linux" \
    org.opencontainers.image.authors="kuwork <kuwork@126.com>" \
    org.opencontainers.image.vendor="K.W. Systems" \
    org.opencontainers.image.version="v10.3.17" \
    org.opencontainers.image.url="https://hub.docker.com/r/kuwork/alpine-mariadb/" \
    org.opencontainers.image.source="https://github.com/kuwork/alpine-mariadb" \
    org.opencontainers.image.revision=$VCS_REF \
    org.opencontainers.image.created=$BUILD_DATE

RUN apk add --no-cache mariadb mariadb-client mariadb-server-utils pwgen && \
    rm -f /var/cache/apk/*

ADD files/run.sh /scripts/run.sh
RUN mkdir /docker-entrypoint-initdb.d && \
    mkdir /scripts/pre-exec.d && \
    mkdir /scripts/pre-init.d && \
    chmod -R 755 /scripts

EXPOSE 3306

VOLUME ["/var/lib/mysql"]

ENTRYPOINT ["/scripts/run.sh"]
