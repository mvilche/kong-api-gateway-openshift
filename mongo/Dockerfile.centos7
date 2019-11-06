FROM centos:7
LABEL AUTOR="MARTIN VILCHE" PROYECTO="MOPNGO CLUSTER"
ENV MONGO_VERSION=https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-rhel70-4.2.0.tgz
RUN mkdir -p /opt/mongodb /opt/mongodb-config /opt/mongodb-data && \
yum -y install libcurl wget netcat net-tools procps sysvinit-tools openssl curl nmap-ncat -y
WORKDIR /opt
RUN wget $MONGO_VERSION && tar zxvf *.tgz --strip-components 1 -C /opt/mongodb && rm -rf *.tgz
RUN adduser -m -u 1001 mongo && chown 1001 -R /opt /home/mongo && \
chgrp -R 0 /opt /home/mongo && \
chmod -R g=u /opt /home/mongo && yum clean all && rm -rf /var/cache/yum
USER 1001
ENV HOME /home/mongo
EXPOSE 27017 27018 27019