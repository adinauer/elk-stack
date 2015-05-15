FROM java:8-jre
MAINTAINER Alexander Dinauer <alexander@dinauer.at>

ENV LOGSTASH_VERSION 1.4.2

RUN wget https://download.elasticsearch.org/logstash/logstash/logstash-${LOGSTASH_VERSION}.tar.gz -O - | tar -xz --directory /opt
RUN mv /opt/logstash-${LOGSTASH_VERSION} /opt/logstash

ADD certificates/logstash.key /opt/logstash/certs/logstash.key
ADD certificates/logstash.crt /opt/logstash/certs/logstash.crt

ADD config/conf.d /opt/logstash/conf.d

EXPOSE 5000

CMD /opt/logstash/bin/logstash agent --config /opt/logstash/conf.d
