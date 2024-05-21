# Dockerfile for rsync client
FROM alpine
LABEL authors="BetaCZ <hlj8080@gmail.com>"

RUN apk add -U rsync \
    && rm -rf /var/cache/apk/*

VOLUME /data

ADD ./run /usr/local/bin/run

ENTRYPOINT ["/usr/local/bin/run"]
