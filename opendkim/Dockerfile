FROM alpine:3.19@sha256:c5b1261d6d3e43071626931fc004f70149baeba2c8ec672bd4f27761f8e1ad6b
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