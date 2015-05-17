FROM java:8-jre
MAINTAINER Alexander Dinauer <alexander@dinauer.at>

ENV ELASTICSEARCH_VERSION 1.5.2

RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-${ELASTICSEARCH_VERSION}.tar.gz -O - | tar -xz --directory /opt && \
	mv /opt/elasticsearch-${ELASTICSEARCH_VERSION} /opt/elasticsearch

EXPOSE 9200 9300

CMD /opt/elasticsearch/bin/elasticsearch
