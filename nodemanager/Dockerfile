FROM fhamster/hadoop-base:hadoop3.2.1-java8-0.1

MAINTAINER GaoXin <gaoxin459716010@163.com>

HEALTHCHECK CMD curl -f http://localhost:8042/ || exit 1

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 8042

CMD ["/run.sh"]
