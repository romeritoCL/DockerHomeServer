FROM graylog/graylog

COPY udp-input-graylog.json /usr/share/graylog/data/contentpacks/udp-input-graylog.json
COPY graylog.conf /usr/share/graylog/data/config/graylog.conf

ENV GRAYLOG_CONTENT_PACKS_AUTO_LOAD udp-input-graylog.json
ENV GRAYLOG_CONTENT_PACKS_LOADER_ENABLED true
ENV GRAYLOG_CONTENT_PACKS_DIR data/contentpacks
