ARG SPARK_VERSION
ARG HADOOP_VERSION=2.7

FROM fhuertas/spark-base:${SPARK_VERSION}-hadoop${HADOOP_VERSION}

MAINTAINER Francisco Huertas <pacohuertas@gmail.com>

COPY master.sh /

ENV SPARK_MASTER_PORT 7077
ENV SPARK_MASTER_WEBUI_PORT 8080
ENV SPARK_MASTER_LOG "${SPARK_HOME}/logs"

EXPOSE 8080 7077 6066

CMD ["/bin/bash", "/master.sh"]
