FROM alpine:3.20@sha256:1e42bbe2508154c9126d48c2b8a75420c3544343bf86fd041fb7527e017a4b4a
EXPOSE 12301

RUN apk --update add \
    opendkim \
    opendkim-utils \
    rsyslog && mkdir -p /var/spool/rsyslog

COPY opendkim.conf /etc/opendkim/opendkim.conf
COPY rsyslog.conf /etc/rsyslog.conf

RUN mkdir -p /etc/opendkim/keys && \
    chmod -R 770 /etc/opendkim/keys && \
    chgrp opendkim /etc/opendkim/keys && \
    mkdir -p /var/run/opendkim/

ENTRYPOINT ["/bin/sh", "-c", "rsyslogd -n & sleep 1; /usr/sbin/opendkim -f"]