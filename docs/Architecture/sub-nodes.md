
# Sub-Nodes


---

## sdb-feed


---

## sdb-fd

人臉辨識服務

符合條件的環境下, 可用 GPU 加速

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


---

## gaziru-parser

此程式目前必須被直接置於 `gaziru` 資料夾中

啟動後會自動執行 `gaziru` 資料夾中的 `run_1920x1080_run_local.bat`

並 parse 輸出的結果, 把 HIT 送給主系統 sdb-nexus

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
