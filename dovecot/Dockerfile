FROM alpine:3.20@sha256:a4f4213abb84c497377b8544c81b3564f313746700372ec4fe84653e4fb03805
EXPOSE 143 993
RUN addgroup -g 103 -S dovemail && adduser --ingroup dovemail --uid 102 --system --no-create-home --disabled-password dovemail

RUN apk update && apk add \
    dovecot \
    dovecot-ldap \
    dovecot-lmtpd && \
    mkdir /mail && \
    chown dovemail:dovemail /mail

ENTRYPOINT ["/usr/sbin/dovecot", "-F"]