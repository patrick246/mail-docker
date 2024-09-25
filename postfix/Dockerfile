FROM alpine:3.19@sha256:ef8240eeaaeb49c6cc2acae720fb9c21453ef43ef0f4c4158c04297ec3286d1d
EXPOSE 25 587

RUN apk update && apk add \
    postfix \
    postfix-ldap \
    postfix-pcre \
    postfix-policyd-spf-perl \
    nmap-ncat

ENTRYPOINT ["/bin/sh", "-c", "/usr/libexec/postfix/post-install create-missing && /usr/sbin/postfix start-fg | tee /var/log/postfix.log"]