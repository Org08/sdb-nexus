
# Architecture

## sdb-nexus

系統核心, 連結所有服務節點

- 由 channel 來區隔每組設定

- 每個 channel 可以設定是否啟用 `影像串流` `人臉偵測` `人臉辨識`  `性別年齡等分析` `商品辨識`

- 每個 channel 在有 `人臉辨識` 的情況下, 可設定是否要啟用 `觸發TCP訊息` `觸發UDP訊息` `觸發HTTP-POST`

- 每個 channel 可以透過前端元件, 訂閱接收 `單張影像` `偵測到的人臉資料` `辨識到人臉的會員資料` `性別年齡等分析的即時資料` `商品辨識資料`

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


#### 設定檔

```javascript
{
    "loglv": "info",                                    // 待棄用, 由 log 取代
    "mongodb": "mongodb://localhost:27017/sdb-nexus",   // mongodb 連線
    "server": {                                         // 本系統的 port
        "http_port": 8080,
        "https_port": 8443
    },
    "store": {                                          // 內建 store.checkout 介面的咖啡按鈕資料
        "coffee": {
            "code": "coffee_0",
            "name": "咖啡",
            "price": 50
        }
    },
    "log": {                                            // 每種 log 的設定值
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
    "logOpts": {                                    // 寫入 db 的 log 的保存及刪除設定
        "keepDays": 7,
        "delAtHour": 0,
        "delAtMinute": 0
    }
}
```

#### 




---

[sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-nexus.md)

[sdb-feed](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-feed.md)

[sdb-fd](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-fd.md)

[sdb-web](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-web.md)

[gaziru-parser](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/gaziru-parser.md)
