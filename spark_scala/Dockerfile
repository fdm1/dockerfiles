FROM gettyimages/spark:2.1.0-hadoop-2.7
MAINTAINER https://github.com/fdm1

ENV LD_LIBRARY_PATH $HADOOP_HOME/lib/native:$LD_LIBRARY_PATH

# # Install sbt for scala files
RUN apt-get update && \
    apt-get install -y apt-transport-https && \
    echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 642AC823 && \
    apt-get update && \
    apt-get install -y sbt && \
    sbt about

