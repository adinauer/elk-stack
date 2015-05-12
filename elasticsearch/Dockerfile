FROM java:8-jre
MAINTAINER Alexander Dinauer <alexander@dinauer.at>

ENV ELASTICSEARCH_NAME elasticsearch-1.5.2

RUN wget -O /tmp/elasticsearch.tar.gz https://download.elastic.co/elasticsearch/elasticsearch/$ELASTICSEARCH_NAME.tar.gz
RUN cd /tmp && \
    tar -xzf elasticsearch.tar.gz && \
    mv $ELASTICSEARCH_NAME /opt/elasticsearch && \
    rm elasticsearch.tar.gz

VOLUME [ "/data" ]

ADD elasticsearch.yml /opt/elasticsearch/config/elasticsearch.yml

WORKDIR /data

EXPOSE 9200

CMD /opt/elasticsearch/bin/elasticsearch

