FROM fdm1/spark:2.1.1

ARG MAVEN_VERSION=3.5.2
ARG MAVEN_BINARY_ARCHIVE_NAME=apache-maven-${MAVEN_VERSION}
ARG MAVEN_BINARY_DOWNLOAD_URL=http://www.trieuvan.com/apache/maven/maven-3/${MAVEN_VERSION}/binaries/${MAVEN_BINARY_ARCHIVE_NAME}-bin.tar.gz

ENV MAVEN_HOME    /usr/local/maven
ENV PATH        $JAVA_HOME/bin:$MAVEN_HOME/bin:$PATH

RUN wget -qO - ${MAVEN_BINARY_DOWNLOAD_URL} | tar -xz -C /usr/local/  && \
    cd /usr/local/ && \
    ln -s ${MAVEN_BINARY_ARCHIVE_NAME} maven
