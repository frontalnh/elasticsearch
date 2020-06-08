# ElasticSearch

## Start and stop

Start `sudo systemctl start elasticsearch.service`
Stop `sudo systemctl stop elasticsearch.service`

## Configuration



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

**쓰기 권한 열어주기**

```sh
curl -XPUT localhost:9200/_settings? \
  -d '{"index": {"blocks": {"read_only_allow_delete": "true"}}}' \
  -H 'Content-Type: application/json'


curl -XPUT localhost:9200/<YOUR_INDEX_NAME>/_settings? \
  -d '{"index": {"blocks": {"read_only_allow_delete": "true"}}}' \
  -H 'Content-Type: application/json'


# kibana elastic search 삭제권한 주기
curl -XPUT localhost:9200/.kibana/_settings? \
  -d '{"index": {"blocks": {"read_only_allow_delete": "false"}}}' \
  -H 'Content-Type: application/json'
```


**Insert data**

```sh
curl -X POST -H "Content-Type:application/json" \
 localhost:9200/user_index/user/<DOCUMENT_ID> \
 -d '{"name":"namhoon"}' 
```

**Retrieve data**

```sh
curl -XGET -H 'Content-Type: application/json' \
  localhost:9200/user_balance_index/user_balance/_search \
  -d '{"sort":[{"start_date":{"order":"desc"}}]}'
```

**DELETE ELASTIC SEARCH INDEX**

```sh
curl -X DELETE localhost:9200/company_index
```
