FROM alpine:3.19@sha256:51b67269f354137895d43f3b3d810bfacd3945438e94dc5ac55fdac340352f48
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