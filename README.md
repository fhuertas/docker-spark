[![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/big-data-europe/Lobby)
# Spark docker


## Build

```bash
# Base
docker build base/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-base:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
# Worker
docker build worker/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-worker:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
# Master
docker build master/ --build-arg SPARK_VERSION=$SPARK_VERSION --build-arg HADOOP_VERSION=${HADOOP_VERSION} -t fhuertas/spark-master:${SPARK_VERSION}-hadoop${HADOOP_VERSION}
```
