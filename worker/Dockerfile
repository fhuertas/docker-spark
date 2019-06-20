ARG SPARK_VERSION
ARG HADOOP_VERSION=2.7

FROM fhuertas/spark-base:${SPARK_VERSION}-hadoop${HADOOP_VERSION}

MAINTAINER Erika Pauwels <erika.pauwels@tenforce.com>
MAINTAINER Gezim Sejdiu <g.sejdiu@gmail.com>

COPY worker.sh /

ENV SPARK_WORKER_WEBUI_PORT 8081
ENV SPARK_WORKER_LOG "${SPARK_HOME}/logs"
ENV SPARK_MASTER "spark://spark-master:7077"

EXPOSE 8081

CMD ["/bin/bash", "/worker.sh"]
