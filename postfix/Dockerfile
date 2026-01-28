FROM alpine:3.20@sha256:a4f4213abb84c497377b8544c81b3564f313746700372ec4fe84653e4fb03805
EXPOSE 25 587

RUN apk update && apk add \
    postfix \
    postfix-ldap \
    postfix-pcre \
    postfix-policyd-spf-perl \
    nmap-ncat

ENTRYPOINT ["/bin/sh", "-c", "/usr/libexec/postfix/post-install create-missing && /usr/sbin/postfix start-fg | tee /var/log/postfix.log"]