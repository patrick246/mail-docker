FROM alpine:3.20@sha256:d9e853e87e55526f6b2917df91a2115c36dd7c696a35be12163d44e6e2a4b6bc
EXPOSE 143 993
RUN addgroup -g 103 -S dovemail && adduser --ingroup dovemail --uid 102 --system --no-create-home --disabled-password dovemail

RUN apk update && apk add \
    dovecot \
    dovecot-ldap \
    dovecot-lmtpd && \
    mkdir /mail && \
    chown dovemail:dovemail /mail

ENTRYPOINT ["/usr/sbin/dovecot", "-F"]