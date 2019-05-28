# Spark base

The Spark base image serves as a base image for the Spark master, Spark worker and Spark submit images.

To generate run

```
docker build . --build-arg SPARK_VERSION=2.4.3 --build-arg HADOOP_VERSION=2.7 -t fhuertas/spark-base:2.4.0-hadoop2.7
```
