FROM alpine:3.10

RUN apk add --no-cache --update busybox-suid shadow busybox-extras curl && \
mkdir -p /opt/prometheus /opt/prometheus-config /opt/prometheus-data && \
wget https://github.com/prometheus/prometheus/releases/download/v2.13.1/prometheus-2.13.1.linux-amd64.tar.gz -O /tmp/prometheus.tar.gz && \
tar zxvf /tmp/prometheus.tar.gz --strip-components 1 -C /opt/prometheus && \
rm -rf /tmp/prometheus.tar.gz

RUN adduser -H -D -u 1001 openshift && usermod -aG 0 openshift && \
chown -R 1001 /opt && \
chgrp -R 0 /opt  && \
chmod -R g=u /opt

USER 1001

EXPOSE 9090

CMD /opt/prometheus/prometheus --config.file=/opt/prometheus-config/prometheus.yml --storage.tsdb.path=/opt/prometheus-data