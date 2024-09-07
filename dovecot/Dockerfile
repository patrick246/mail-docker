FROM alpine:3.19@sha256:ae65dbf8749a7d4527648ccee1fa3deb6bfcae34cbc30fc67aa45c44dcaa90ee
EXPOSE 143 993
RUN addgroup -g 103 -S dovemail && adduser --ingroup dovemail --uid 102 --system --no-create-home --disabled-password dovemail

RUN apk update && apk add \
    dovecot \
    dovecot-ldap \
    dovecot-lmtpd && \
    mkdir /mail && \
    chown dovemail:dovemail /mail

ENTRYPOINT ["/usr/sbin/dovecot", "-F"]