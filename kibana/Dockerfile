FROM buildpack-deps:sid-curl
MAINTAINER Alexander Dinauer <alexander@dinauer.at>

ENV KIBANA_VERSION 4.0.2-linux-x64

RUN wget https://download.elasticsearch.org/kibana/kibana/kibana-${KIBANA_VERSION}.tar.gz -O - | tar -xz --directory /opt
RUN mv /opt/kibana-${KIBANA_VERSION} /opt/kibana


EXPOSE 5601

CMD /opt/kibana/bin/kibana
