FROM alpine:3.19
EXPOSE 143 993
RUN addgroup -g 103 -S dovemail && adduser --ingroup dovemail --uid 102 --system --no-create-home --disabled-password dovemail

RUN apk update && apk add \
    dovecot \
    dovecot-ldap \
    dovecot-lmtpd && \
    mkdir /mail && \
    chown dovemail:dovemail /mail

ENTRYPOINT ["/usr/sbin/dovecot", "-F"]