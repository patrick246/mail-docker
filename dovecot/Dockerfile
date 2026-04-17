FROM alpine:3.23@sha256:5b10f432ef3da1b8d4c7eb6c487f2f5a8f096bc91145e68878dd4a5019afde11
EXPOSE 143 993
RUN addgroup -g 103 -S dovemail && adduser --ingroup dovemail --uid 102 --system --no-create-home --disabled-password dovemail

RUN apk update && apk add \
    dovecot \
    dovecot-ldap \
    dovecot-lmtpd && \
    mkdir /mail && \
    chown dovemail:dovemail /mail

ENTRYPOINT ["/usr/sbin/dovecot", "-F"]