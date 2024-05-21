# Dockerfile for rsync server
FROM alpine
LABEL authors="BetaCZ <hlj8080@gmail.com>"

RUN apk add -U rsync \
    && rm -rf /var/cache/apk/*

VOLUME /synced
EXPOSE 873

ADD ./run /usr/local/bin/run

ENTRYPOINT ["/usr/local/bin/run"]
