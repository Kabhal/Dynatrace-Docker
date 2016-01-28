FROM alpine:3.3

MAINTAINER Martin Etmajer <martin.etmajer@dynatrace.com>

ENV DT_AGENT_VERSION   "6.2"
ENV DT_AGENT_FILE_NAME "dynatrace-agent-unix.jar"
ENV DT_AGENT_URL       "http://downloads.dynatracesaas.com/${DT_AGENT_VERSION}/${DT_AGENT_FILE_NAME}"

ENV DT_AGENT_HOME      "/opt/dynatrace"
ENV DT_AGENT_LIB64     "${DT_AGENT_HOME}/agent/lib64/libdtagent.so"

ENV DT_INSTALL_DEPS    "curl openjdk8-jre-base"

RUN apk add --no-cache ${DT_INSTALL_DEPS} && \
    curl -L -o /tmp/${DT_AGENT_FILE_NAME} ${DT_AGENT_URL} && \
    java -jar /tmp/${DT_AGENT_FILE_NAME} -b 64 -t ${DT_AGENT_HOME} -y && \
    apk del ${DT_INSTALL_DEPS} && \
    rm -rf /tmp/*

CMD while true; do sleep 1; done