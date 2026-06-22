# Logstash with OpenSearch output plugin pre-installed, for use with the ECK
# Operator. The official Logstash image does not bundle the OpenSearch output
# plugin; installing it via initContainer adds 5+ minutes to startup. This
# image installs the plugin at build time.
#
# Usage:
#   docker build -t logstash-with-opensearch-plugin:8.19.0 .
#   docker run --rm -it \
#     -v $(pwd)/pipeline:/usr/share/logstash/pipeline \
#     logstash-with-opensearch-plugin:8.19.0

FROM docker.elastic.co/logstash/logstash:8.19.0

LABEL maintainer="Younsung Lee <cysl@kakao.com>" \
      org.opencontainers.image.title="logstash-with-opensearch-plugin" \
      org.opencontainers.image.description="Logstash with OpenSearch output plugin and Asia/Seoul timezone" \
      org.opencontainers.image.version="8.19.0" \
      org.opencontainers.image.base.name="docker.elastic.co/logstash/logstash:8.19.0" \
      org.opencontainers.image.source="https://github.com/opencomputinggarage/containers" \
      org.opencontainers.image.deprecated="false"

USER root
RUN apt-get update \
    && apt-get install -y --no-install-recommends tzdata \
    && rm -rf /var/lib/apt/lists/*
USER logstash

ENV TZ=Asia/Seoul

RUN bin/logstash-plugin install logstash-output-opensearch \
    && bin/logstash-plugin list
