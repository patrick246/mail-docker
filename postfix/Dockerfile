FROM alpine:3.19@sha256:ae65dbf8749a7d4527648ccee1fa3deb6bfcae34cbc30fc67aa45c44dcaa90ee
EXPOSE 25 587

RUN apk update && apk add \
    postfix \
    postfix-ldap \
    postfix-pcre \
    postfix-policyd-spf-perl \
    nmap-ncat

ENTRYPOINT ["/bin/sh", "-c", "/usr/libexec/postfix/post-install create-missing && /usr/sbin/postfix start-fg | tee /var/log/postfix.log"]