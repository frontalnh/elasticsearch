# Kibana

## Installation

```
```

## TroubleShooting

default space 를 만들지 못해 자꾸 space 로 이동하는 문제.
이거 시스템 스토리지가 작으면 자동으로 kibana 가 아래 세팅을 사용하기 때문에 유의할것.
FORBIDDEN/12/index read-only / allow delete (api)]
아래 두개를 안해주면 kibana 가 쓰기작업을 못함...

```json
PUT .kibana/_settings
{
"index": {
"blocks": {
"read_only_allow_delete": "false"
}
}
}

}
```