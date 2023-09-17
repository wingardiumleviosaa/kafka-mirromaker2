FROM openjdk:11-jre-slim

ENV KAFKA_VERSION=3.5.1 \
    SCALA_VERSION=2.13 \
    WORK_HOME=/opt/

ENV KAFKA_RELEASE=kafka_${SCALA_VERSION}-${KAFKA_VERSION}

WORKDIR ${WORK_HOME}

RUN apt-get update &&\
    apt-get install -y curl &&\
    apt-get install -y ca-certificates

RUN curl -LO https://downloads.apache.org/kafka/"${KAFKA_VERSION}"/"${KAFKA_RELEASE}".tgz
RUN tar xf ${KAFKA_RELEASE}.tgz &&\
    mv ${KAFKA_RELEASE} kafka/ &&\
    rm -rf ${KAFKA_RELEASE}.tgz

COPY --chown=1000:1000 run.sh  /run.sh
COPY --chown=1000:1000 mm2.properties /opt/kafka/config/mm2.properties

ENTRYPOINT ["/bin/bash", "-c"]
CMD ["/run.sh"]
