FROM alpine:3.20@sha256:780405de0f7cf99f985dd5a4f04dfc5aae71509d89505c1ba48a88d95a0ceb7f
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