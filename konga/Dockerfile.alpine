FROM alpine:3.10

RUN apk add --no-cache --update git curl busybox-suid shadow busybox-extras nodejs npm

WORKDIR /opt

RUN adduser -D -u 1001 konga && usermod -aG 0 konga && \
chown -R 1001 /home/konga /opt

USER 1001
 
RUN git clone https://github.com/pantsel/konga.git && cd konga && \
npm set audit false && \
npm install sails bower gulp && \
npm install

USER root

COPY run /usr/bin/run

RUN mkdir -p /opt/konga/custom_config && chown -R 1001 /usr/bin/run /home/konga /opt && \
chgrp -R 0 /usr/bin/run /home/konga /opt && \
chmod -R g=u /usr/bin/run /home/konga /opt

USER 1001

EXPOSE 1337

WORKDIR /opt/konga

CMD ["/usr/bin/run"]
