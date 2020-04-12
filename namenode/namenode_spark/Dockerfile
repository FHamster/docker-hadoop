FROM fhamster/hadoop-namenode:hadoop3.2.1-java8-0.1

MAINTAINER GaoXin <gaoxin459716010@163.com>

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1
ENV SPARK_VERSION 2.4.5

ENV SPARK_URL https://mirrors.sonic.net/apache/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-without-hadoop.tgz
#ENV SPARK_URL https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-without-hadoop.tgz

#RUN apk add --no-cache wget \
RUN  curl -fSL "$SPARK_URL" -o spark-${SPARK_VERSION}-bin-without-hadoop.tgz \
# && wget ${SPARK_URL} \
 && tar -xvzf spark-${SPARK_VERSION}-bin-without-hadoop.tgz \
 && mv spark-${SPARK_VERSION}-bin-without-hadoop spark \
 && rm spark-${SPARK_VERSION}-bin-without-hadoop.tgz \
 && cd /

ENV SPARK_HOME /spark/
COPY spark-env.sh /spark/conf/

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 9870

CMD ["/run.sh","/bin/bash"]