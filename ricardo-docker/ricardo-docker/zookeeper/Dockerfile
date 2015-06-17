# Dockerfile to setup a ZooKeeper 3.4.6 image
FROM centos:6.6
MAINTAINER sbardy <szabolcs.bardy@ricardo.ch>

ENV ZOOKEEPER_VERSION 3.4.6
ENV ZOOKEEPER zookeeper-$ZOOKEEPER_VERSION

RUN yum -y update && \
  yum -y install java-1.7.0-openjdk.x86_64 && \
  yum -y install wget && \
  yum -y install tar && \
  yum -y install unzip && \
  wget -nv --output-document=/opt/zookeeper-3.4.6.tgz http://apache.mirrors.pair.com/zookeeper/$ZOOKEEPER/$ZOOKEEPER.tar.gz && \
  tar -xf /opt/$ZOOKEEPER.tgz -C /opt && \
  rm /opt/$ZOOKEEPER.tgz && \
  ln -s /opt/$ZOOKEEPER /opt/zookeeper && \
  cp /opt/zookeeper/conf/zoo_sample.cfg /opt/zookeeper/conf/zoo.cfg && \
  mkdir -p /var/lib/zookeeper 

EXPOSE 2181 2888 3888

WORKDIR /opt/zookeeper

VOLUME ["/opt/zookeeper/conf", "/var/lib/zookeeper"]

ENTRYPOINT ["/opt/zookeeper/bin/zkServer.sh"]
CMD ["start-foreground"]
