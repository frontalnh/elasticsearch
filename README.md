# ElasticSearch

## Start and stop

Start `sudo systemctl start elasticsearch.service`
Stop `sudo systemctl stop elasticsearch.service`

## Interact with elasticsearch

**Check clustur status**

```sh
curl -X GET http://localhost:9200/_cluster/health?pretty=true
```

여기서 yellow 상태는 데이터 읽기 쓰기가 모두 가능한 상태이지만, replica shard 가 아직 배정되지 않는 상태입니다.
하나의 노드에서는 replica 를 배정하지 못해서 yellow 상태!

**Check index and shard**

```sh
# Check indexs
curl -X GET localhost:9200/_cat/indices?v

# Check shard, v for verbose
# You can check shard is primary and replica
curl -X GET localhost:9200/_cat/shards?v
```

**Set not to have replica**

```sh
curl -X PUT localhost:9200/_settings?pretty \
  -d '{"index":{"number_of_replicas": 0}}' \
  -H 'Content-Type: application/json'
```

**Insert data**

```sh
curl -X POST -H "Content-Type:application/json" \
 localhost:9200/user_index/user/_create \
 -d '{"name":"namhoon"}'
```

**Retrieve data**

```sh
curl localhost:9200/company/employee/_search | jq
```

**DELETE ELASTIC SEARCH INDEX**

```sh
curl -X DELETE localhost:9200/company_index
```

# Logstash

Logstash is an open source data collection engine with real-time pipelining capabilities.

## Installation

Start logstash with standard input

```
sudo /usr/share/logstash/bin/logstash -e 'input { stdin {} } output { stdout {} }'
```

Start logstash service

```sh
sudo systemctl start logstash.service
sudo systemctl stop logstash.service
```

## Reset sql_last_value

```

```

## Working with plugins

List

```sh
logstash-plugin list
logstash-plugin list --verbose
```

### JDBC Input Plugin


# Kibana

## Installation

```
```