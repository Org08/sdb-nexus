
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

- 符合條件的環境下, 可用 GPU 加速

#### 設定

```javascript
{
    "loglv": "debug",                   // 設定會印出的 log 等級
    "log_filter": {
        "fps": false                    // 設定是否要持續印出 fps 資訊
    },
    "path": {
        "licence": "./licence"          // licence key 路徑
    },
    "server": {                         
        "ip": "192.168.11.14",          // sdb-nexus 所在的機器的 IP
        "https_port": 4001,             // 本服務在本地對應的 port
        "nexus_port": 9001              // 本服務開給 sdb-nexus 連的 port
    },
    "channelID": 1,                     // 本服務在 sdb-nexus 對應的 channelID
    "hwacc": false,                     // 是否啟用硬體加速. (目前測試無顯著效果, 且有資源分配問題, 暫時都不啟用即可)
    "feed": {                           // 設定提供的影像. 若不想開啟, 只要給 false 即可
        "ipcam": {
            "url": "desktop",           // 通常是 ipcam 串流的 RTSP URL, 當給的是 "desktop" 時, 則會傳本機桌面
            "resolution": "1366x728",   // 解析度. 長寬間要用 "x" 連接
            "quality":  3,
            "framerate": 5
        },
        "webcam": true,                 // 接收 webcam 影像. 或是其他單張影像, 例如上傳的照片
        "h264player": {
            "port": 6001,               // 給前端 h264 播放器的 port
            "input": "desktop",         // 通常是 ipcam 串流的 RTSP URL, 當給的是 "desktop" 時, 則會傳本機桌面
            "width": 1280,
            "height": 720,
            "fps": 15
        }
    },
    "fd": {                             // 與 sdb-fd 的相關設定
        "mode": "Multi",                // 未支援其他模式, 不用動 
        "multiTimeoutMS": 500,          // 未支援其他模式, 不用動
        "connection": {
            "socketio": {               // 透過 socketio 與 sdb-fd 溝通
                "host": "localhost",    // 目標 sdb-fd 的 ip
                "port": 3000            // 目標 sdb-fd 的 port
            },
            "nodeipc": {                // 透過 node-ipc 與 sdb-fd 溝通. 當有太高每秒張數傳送問題時, 建議用這種
                "ipc_id": "feed-1",     // 本服務的 ipc id
                "ipc_server_id": "fd-1" // 目標 sdb-fd 的 ipc id
            }
        }
    }

}
```

---

## sdb-fd

人臉辨識服務

- 接收來自 sdb-feed 解出的單張影像, 偵測人臉並回傳

- 符合條件的環境下, 可用 GPU 加速

#### 設定

```javascript
{
    "loglv": "debug",                       // 設定會印出的 log 等級
    "log_filter": {
        "fps": false                        // 設定是否要持續印出 fps 資訊
    },
    "path": {
        "licence": "./licence",             // licence key 路徑
        "opencv": "./dist/opencv",          // opencv 路徑
        "tensorflow": "./dist/tensorflow"   // tensorflow 路徑
    },
    "port": 3000,                           // 開給 sdb-feed 的 port (其實只要符合規範, 其他來源也可以直接連來用)
    "ipc_id": "fd-1",                       // 本服務的 ipc id
    "hwacc": false,                         // 是否啟用硬體加速
    "cv_min_detection": 4                   // 人臉偵測門檻值, 數字越大越嚴格
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

- parse 輸出的結果, 把 HIT 送給主系統 [sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/nexsus.md)

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
