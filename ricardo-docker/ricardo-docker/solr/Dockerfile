# Dockerfile to setup a Solr v5 image
FROM centos:6.6
MAINTAINER sbardy <szabolcs.bardy@ricardo.ch>

ENV SOLR_VERSION 5.1.0
ENV SOLR solr-$SOLR_VERSION
ENV SOLR_USER solr

RUN yum -y update && \
  yum -y install java-1.7.0-openjdk.x86_64 && \
  yum -y install wget && \
  yum -y install tar && \
  yum -y install unzip && \
  groupadd -r $SOLR_USER && \
  useradd -r -g $SOLR_USER $SOLR_USER && \
  mkdir -p /opt && \
  wget -nv --output-document=/opt/$SOLR.tgz http://archive.apache.org/dist/lucene/solr/$SOLR_VERSION/$SOLR.tgz && \
  tar -xf /opt/$SOLR.tgz -C /opt && \ 
  rm /opt/$SOLR.tgz && \ 
  ln -s /opt/$SOLR /opt/solr && \ 
  chown -R $SOLR_USER:$SOLR_USER /opt/solr /opt/$SOLR

EXPOSE 8983
WORKDIR /opt/solr
USER $SOLR_USER
CMD ["/bin/bash", "-c", "/opt/solr/bin/solr -f"]




