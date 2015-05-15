ELK Stack
=========



Elasticsearch
-------------

### Build image

	cd /vagrant/elk-stack/elasticsearch
	docker build -t adinauer/elk-elasticsearch .

### Start container

	docker run -d -p 9200:9200 -v /vagrant/elk-stack/data:/data adinauer/elk-elasticsearch

### Import sample data

	curl -XPOST 'localhost:9200/bank/account/_bulk?pretty' --data-binary @accounts.json

### List indices

	curl '127.0.0.1:9200/_cat/indices?v'



Kibana
------

### Adapt config

Change `elasticsearch_url` in `config/kibana.yml` and use the hosts IP address.

### Build image

	cd /vagrant/elk-stack/kibana
	docker build -t adinauer/elk-kibana .

### Start container

Find the `elasticsearch` container with `docker ps`, then use the container name or ID for the following command.

	docker run -d -p 5601:5601 --link=ES_CONTAINER_NAME:elasticsearch adinauer/elk-kibana

### Setup indices

...



Logstash
--------

### Generate an SSL certificate

	sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout logstash.key -out /logstash.crt

Place the `.crt` and `.key` files in the `certificates` directory.

### Build image

	cd /vagrant/elk-stack/logstash
	docker build -t adinauer/elk-logstash

### Start container

Find the `elasticsearch` container with `docker ps`, then use the container name or ID for the following command.

	docker run -d -p 5000:5000 --link=ES_CONTAINER_NAME:elasticsearch adinauer/elk-logstash



Logstash-Forwarder
------------------

...