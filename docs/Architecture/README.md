
# Architecture

## sdb-nexus



設定檔

```javascript
{
    "loglv": "info",
    "mongodb": "mongodb://localhost:27017/sdb-nexus",
    "server": {
        "http_port": 8080,
        "https_port": 8443
    },
    "store": {
        "coffee": {
            "code": "coffee_0",
            "name": "咖啡",
            "price": 50
        }
    },
    "log": {
        "sys": {
            "level": "info",
            "enabled": true
        },
        "channel": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "member": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "store": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "storeItem": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "fa": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "fr": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "feed": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "gaziru": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "tcp": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "udp": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "frsdb": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "baofeng": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "frRecord": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "pts": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "trigger": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "conf": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        },
        "h264player": {
            "level": "info",
            "enabled": true,
            "channelCnt": 20
        }
    },
    "logOpts": {
        "keepDays": 7,
        "delAtHour": 0,
        "delAtMinute": 0
    }
}
```


backend

- mongodb

- frs db

- frs socket server

- fa

- gaziru

- sdb-feed

- sdb-fd

- sdb-web

- baofeng

frontend

- api

- monitor

- h264player

- h264insec

- store

- console


---

[sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-nexus.md)

[sdb-feed](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-feed.md)

[sdb-fd](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-fd.md)

[sdb-web](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-web.md)

[gaziru-parser](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/gaziru-parser.md)
