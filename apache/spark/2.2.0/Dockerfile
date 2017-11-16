FROM openjdk:8u151-jdk

ARG SPARK_VERSION=2.2.0
ARG SPARK_BINARY_ARCHIVE_NAME=spark-${SPARK_VERSION}-bin-without-hadoop
ARG SPARK_BINARY_DOWNLOAD_URL=http://d3kbcqa49mib13.cloudfront.net/${SPARK_BINARY_ARCHIVE_NAME}.tgz

ARG HADOOP_VERSION=2.8.2
ARG HADOOP_BINARY_ARCHIVE_NAME=hadoop-${HADOOP_VERSION}
ARG HADOOP_BINARY_DOWNLOAD_URL=http://archive.apache.org/dist/hadoop/common/${HADOOP_BINARY_ARCHIVE_NAME}/${HADOOP_BINARY_ARCHIVE_NAME}.tar.gz

ENV HADOOP_HOME     /usr/local/hadoop
ENV SPARK_HOME      /usr/local/spark
ENV LD_LIBRARY_PATH $HADOOP_HOME/lib/native

RUN wget -qO - ${HADOOP_BINARY_DOWNLOAD_URL} | tar -xz -C /usr/local/ && \
    wget -qO - ${SPARK_BINARY_DOWNLOAD_URL} | tar -xz -C /usr/local/ && \
    rm -rf $HADOOP_HOME/share/doc && \
    cd /usr/local/ && \
    ln -s ${HADOOP_BINARY_ARCHIVE_NAME} hadoop && \
    ln -s ${SPARK_BINARY_ARCHIVE_NAME} spark && \
    cp spark/conf/log4j.properties.template spark/conf/log4j.properties
    # sed -i -e s/WARN/ERROR/g spark/conf/log4j.properties && \
    # sed -i -e s/INFO/ERROR/g spark/conf/log4j.properties

ENV HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop
ENV SPARK_DIST_CLASSPATH="$HADOOP_HOME/etc/hadoop/*:$HADOOP_HOME/share/hadoop/common/lib/*:$HADOOP_HOME/share/hadoop/common/*:$HADOOP_HOME/share/hadoop/hdfs/*:$HADOOP_HOME/share/hadoop/hdfs/lib/*:$HADOOP_HOME/share/hadoop/hdfs/*:$HADOOP_HOME/share/hadoop/yarn/lib/*:$HADOOP_HOME/share/hadoop/yarn/*:$HADOOP_HOME/share/hadoop/mapreduce/lib/*:$HADOOP_HOME/share/hadoop/mapreduce/*:$HADOOP_HOME/share/hadoop/tools/lib/*"

RUN apt-get update && apt-get install -y python-pip
RUN pip install ipython
ENV PYSPARK_DRIVER_PYTHON ipython
ENV PATH            $SPARK_HOME/bin:$SPARK_HOME/sbin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$PATH

CMD ["/usr/local/spark/bin/spark-shell"]
