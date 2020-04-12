FROM fhamster/hadoop-base:hadoop3.2.1-java8-0.1

MAINTAINER GaoXin <gaoxin459716010@163.com>

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1

RUN apk add --no-cache vim

#ENV HDFS_NAMENODE_USER="root"
#ENV HDFS_DATANODE_USER="root"
#ENV HDFS_SECONDARYNAMENODE_USER="root"
#ENV YARN_RESOURCEMANAGER_USER="root"
#ENV YARN_NODEMANAGER_USER="root"
ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
RUN mkdir -p /hadoop/dfs/name
VOLUME /hadoop/dfs/name

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 9870

CMD ["/run.sh","/bin/bash"]
