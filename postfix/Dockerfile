FROM alpine:3.19@sha256:af4785ccdbcd5cde71bfd5b93eabd34250b98651f19fe218c91de6c8d10e21c5
EXPOSE 25 587

RUN apk update && apk add \
    postfix \
    postfix-ldap \
    postfix-pcre \
    postfix-policyd-spf-perl \
    nmap-ncat

ENTRYPOINT ["/bin/sh", "-c", "/usr/libexec/postfix/post-install create-missing && /usr/sbin/postfix start-fg | tee /var/log/postfix.log"]