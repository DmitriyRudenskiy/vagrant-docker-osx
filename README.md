# vagrant-docker-osx

docker pull elasticsearch
docker pull kibana
docker pull rabbitmq


docker run -d -v "/disk/esdata":/usr/share/elasticsearch/data elasticsearch
docker run --name some-kibana --link some-elasticsearch:elasticsearch -p 5601:5601 -d kibana
