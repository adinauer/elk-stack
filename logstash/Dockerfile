FROM java:8-jre
MAINTAINER Alexander Dinauer <alexander@dinauer.at>

ENV LOGSTASH_VERSION 1.4.2

RUN wget https://download.elasticsearch.org/logstash/logstash/logstash-${LOGSTASH_VERSION}.tar.gz -O - | tar -xz --directory /opt
RUN mv /opt/logstash-${LOGSTASH_VERSION} /opt/logstash


EXPOSE 5000

CMD /opt/logstash/bin/logstash agent --config /opt/logstash/conf.d
