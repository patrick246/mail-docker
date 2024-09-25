FROM alpine:3.19@sha256:ef8240eeaaeb49c6cc2acae720fb9c21453ef43ef0f4c4158c04297ec3286d1d
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