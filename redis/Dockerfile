FROM alpine:3.10

RUN apk add --no-cache --update redis busybox-suid shadow busybox-extras && \
mkdir -p /opt/redis /opt/redis-config /var/run/redis && \
adduser -H -D -u 1001 openshift && usermod -aG 0 openshift && \
chown -R 1001 /opt && \
chgrp -R 0 /opt  && \
chmod -R g=u /opt

USER 1001

EXPOSE 6379

CMD redis-server /opt/redis-config/redis.conf