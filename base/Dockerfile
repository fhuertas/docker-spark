FROM java:openjdk-8-jre

MAINTAINER Francisco Huertas <pacohuertas@gmail.com>

ENV ENABLE_INIT_DAEMON true
ENV INIT_DAEMON_BASE_URI http://identifier/init-daemon
ENV INIT_DAEMON_STEP spark_master_init

ARG SPARK_VERSION
ARG HADOOP_VERSION
ARG PYTHON_VERSION="python3"
ENV SPARK_HOME=/opt/spark
ENV PATH="/opt/spark/bin:${PATH}"
ENV PYSPARK_PYTHON=${PYTHON_VERSION}

COPY wait-for-step.sh /
COPY execute-step.sh /
COPY finish-step.sh /

#COPY bde-spark.css /css/org/apache/spark/ui/static/timeline-view.css
RUN apt-get update; \
    apt-get install -y curl \
          python  \
          python3  \
          python3-setuptools \
          python3-pip; \
    chmod +x *.sh; \
    pip3 install ipython; \
    wget https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz; \
    tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz; \
    mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} ${SPARK_HOME}; \
    rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz; \
    mv ${SPARK_HOME}/conf/log4j.properties.template ${SPARK_HOME}/conf/log4j.properties; \
    sed -i 's/log4j.rootCategory.*/log4j.rootCategory=WARN, console/' ${SPARK_HOME}/conf/log4j.properties; \
    rm -rf /var/lib/apt/lists/*; \
    chmod +x /wait-for-step.sh && chmod +x /execute-step.sh && chmod +x /finish-step.sh

# Fix the value of PYTHONHASHSEED
# Note: this is needed when you use Python 3.3 or greater
ENV PYTHONHASHSEED 1
