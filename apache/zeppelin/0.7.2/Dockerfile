FROM fdm1/spark:2.1.1

ARG ZEPPELIN_VERSION=0.7.2
ARG ZEPPELIN_BINARY_ARCHIVE_NAME=zeppelin-${ZEPPELIN_VERSION}-bin-netinst
ARG ZEPPELIN_BINARY_DOWNLOAD_URL=http://apache.uberglobalmirror.com/zeppelin/zeppelin-${ZEPPELIN_VERSION}/${ZEPPELIN_BINARY_ARCHIVE_NAME}.tgz

ARG INTERPRETERS=md,shell,jdbc,python

ENV PATH $ZEPPELIN_HOME/bin:$PATH

RUN wget -qO - ${ZEPPELIN_BINARY_DOWNLOAD_URL} | tar -xz -C /usr/local/ && \
    cd /usr/local/ && \
    ln -s ${ZEPPELIN_BINARY_ARCHIVE_NAME} zeppelin && \
    /usr/local/zeppelin/bin/install-interpreter.sh --name ${INTERPRETERS} 

CMD ["/usr/local/zeppelin/bin/zeppelin.sh", "start"]
