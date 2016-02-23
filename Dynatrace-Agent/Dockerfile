FROM debian:wheezy

MAINTAINER Martin Etmajer <martin.etmajer@dynatrace.com>

ENV VERSION             "6.2"
ENV INSTALLER_FILE_NAME "dynatrace-agent-unix.jar"
ENV INSTALLER_URL       "http://downloads.dynatracesaas.com/${VERSION}/${INSTALLER_FILE_NAME}"

ENV DT                  "/dynatrace"
ENV LIB32               "${DT}/agent/lib/libdtagent.so"
ENV LIB64               "${DT}/agent/lib64/libdtagent.so"

ENV DT_INSTALL_DEPS "curl openjdk-7-jre-headless"
RUN apt-get update && \
    apt-get install -y --no-install-recommends ${DT_INSTALL_DEPS} && \
    curl -L -o /tmp/${INSTALLER_FILE_NAME} ${INSTALLER_URL} && \
    java -jar /tmp/${INSTALLER_FILE_NAME} -b 64 -t ${DT} -y && \
    apt-get remove --purge -y ${DT_INSTALL_DEPS} $(apt-mark showauto) && \
    rm -rf /var/lib/apt/lists/* /tmp/*

CMD while true; do sleep 1; done