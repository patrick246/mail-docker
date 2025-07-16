FROM alpine:3.20@sha256:b3119ef930faabb6b7b976780c0c7a9c1aa24d0c75e9179ac10e6bc9ac080d0d
EXPOSE 25 587

RUN apk update && apk add \
    postfix \
    postfix-ldap \
    postfix-pcre \
    postfix-policyd-spf-perl \
    nmap-ncat

ENTRYPOINT ["/bin/sh", "-c", "/usr/libexec/postfix/post-install create-missing && /usr/sbin/postfix start-fg | tee /var/log/postfix.log"]