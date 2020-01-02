
# Sub-Nodes

負責各種功能的子節點

可以跟主系統在同樣的機器執行, 也可以視需要分散配置

---

## sdb-feed

影像服務

- 接收 ipcam 或 webcam 的影像

- 解出或轉發單張影像給 sdb-fd 偵測人臉

- 提供給前端 h264 播放器即時串流

- 提供給 sdb-nexus 持續更新的單張 frame

- 轉發來自 sdb-fd 偵測出的人臉資料給 sdb-nexus

#### 設定

```javascript
{
    "loglv": "debug",
    "log_filter": {
        "fps": false
    },
    "path": {
        "licence": "./licence"
    },
    "server": {
        "ip": "192.168.11.14",
        "https_port": 4020,
        "nexus_port": 9020
    },
    "channelID": 1,
    "hwacc": false,
    "feed": {
        "ipcam": {
            "url": "desktop",
            "resolution": "1366x728",
            "quality":  3,
            "framerate": 5
        },
        "webcam": false,
        "h264player": false
    },
    "fd": {
        "mode": "Multi",
        "multiTimeoutMS": 500,
        "connection": {
            "socketio": {
                "host": "localhost",
                "port": 3000
            },
            "nodeipc": {
                "ipc_id": "feed-1",
                "ipc_server_id": "fd-1"
            }
        }
    }

}
```

---

## sdb-fd

人臉辨識服務

- 符合條件的環境下, 可用 GPU 加速

- 接收來自 sdb-feed 解出的單張影像, 偵測人臉並回傳

#### 設定

```javascript
{
    "loglv": "debug",
    "log_filter": {
        "fps": false
    },
    "path": {
        "licence": "./licence",
        "opencv": "./dist/opencv",
        "tensorflow": "./dist/tensorflow"
    },
    "port": 3000,
    "ipc_id": "fd-1",
    "hwacc": false,
    "cv_min_detection": 4
}
```

---

## sdb-web

方便配置前端應用的單純 web server

- 在 static 資料夾中放置網頁檔案即可

- http 及 https 都是跑在預設 port

- 通常會配置在跟 sdb-nexus 同機器上, 不過其實沒有限制

---

## gaziru-parser

與 gaziru 溝通用的程式

- 此程式目前必須被直接置於 `gaziru` 資料夾中

- 啟動後會自動執行 `gaziru` 資料夾中的 `run_1920x1080_run_local.bat`

- parse 輸出的結果, 把 HIT 送給主系統 sdb-nexus

> TODO 連結到 sdb-nexus

#### 連線

程式啟動後, 會同時起一個 `port:8787` 的 socket server

URL 範例

```
ws://[IP]:8787/gaziru
```

#### 事件

當 parse 到 HIT 時

會對每個 websokcet 連線發送 `HIT` 事件

資料範例

```
{
    index: index,
    barcode: barcode
}
```

---
