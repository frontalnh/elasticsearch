# ElasticSearch

## Installation

## Configure and run Elasticsearch

/etc/elasticsearch/elasticsearch.yml

```
network.host: 0.0.0.0
discovery.seed_hosts:
  - Your host ip
```

Start `sudo systemctl start elasticsearch.service`
Stop `sudo systemctl stop elasticsearch.service`

## Interactwith elastic search

Insert data

```
curl -X POST -H "Content-Type:application" \
 localhost:9200/company/employee/_create \
 -d '{"name":"namhoon"}'
```

Retrieve data

```
curl localhost:9200/company/employee/_search | jq
```

# Logstash

Logstash is an open source data collection engine with real-time pipelining capabilities.

## Installation

Start logstash with standard input

```
sudo /usr/share/logstash/bin/logstash -e 'input { stdin {} } output { stdout {} }'
```

Start logstash service

```
sudo systemctl start logstash.service
```

## Working with plugins

List

```
logstash-plugin list
logstash-plugin list --verbose
```

### JDBC Input Plugin
