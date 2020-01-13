# Spark docker

This repository contain the files needed to generate docker images for spark in any spark version. Some images have been generated and they are disponible in docker hub:

+ https://hub.docker.com/r/fhuertas/spark-base
+ https://hub.docker.com/r/fhuertas/spark-master
+ https://hub.docker.com/r/fhuertas/spark-worker

## Build

To generate image for other versions it is needed to run the following commands

```bash
# Set spark version. E.g: 2.4.4
export SPARK_VERSION=2.4.4
# Set haddop version E.g. 2.7
export HADOOP_VERSION=2.7
# Base
docker build base/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-base:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
# Worker
docker build worker/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-worker:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
# Master
docker build master/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-master:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
```
