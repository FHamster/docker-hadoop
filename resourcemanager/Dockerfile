FROM fhamster/hadoop-base:hadoop3.2.1-java8-0.1

MAINTAINER GaoXin <gaoxin459716010@163.com>

HEALTHCHECK CMD curl -f http://localhost:8088/ || exit 1

ENV HDFS_NAMENODE_USER="root"
ENV HDFS_DATANODE_USER="root"
ENV HDFS_SECONDARYNAMENODE_USER="root"
ENV YARN_RESOURCEMANAGER_USER="root"
ENV YARN_NODEMANAGER_USER="root"y

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 8088

CMD ["/run.sh"]
