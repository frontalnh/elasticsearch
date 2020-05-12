
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

## Configuration

**환경 변수 세팅하기**

/etc/default/logstash
```sh
LS_HOME="/usr/share/logstash"
LS_SETTINGS_DIR="/etc/logstash"
LS_PIDFILE="/var/run/logstash.pid"
LS_USER="logstash"
LS_GROUP="logstash"
LS_GC_LOG_FILE="/var/log/logstash/gc.log"
LS_OPEN_FILES="16384"
LS_NICE="19"
SERVICE_NAME="logstash"
SERVICE_DESCRIPTION="logstash"

# ADDED ENVIRONMENT VARIABLE
AWS_ACCESS_KEY_ID=""
AWS_SECRET_ACCESS_KEY=""
```

**마지막 실행 정보 저장하기 -> Last run metadata**

로그스태시가 마지막 실행 정보를 저장하기 위해서 아래처럼 logstash 에게 권한을 준다.

```
sudo chown logstash:logstash /etc/logstash/conf.d/lastrun
```


## Working with plugins

List

```sh
logstash-plugin list
logstash-plugin list --verbose
```

### JDBC Input Plugin


