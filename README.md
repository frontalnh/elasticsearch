# ElasticSearch

## Installation

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

