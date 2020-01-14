
# Pages



---

## api

只能用瀏覽器的開發者介面使用

在該介面的 console 分頁中用輸入指令的方式來控制

詳細使用方式可參考 [SrAPI](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/README.md)


#### url

```javascript
https://[server_id]:8443/api
```

---

## console

圖形介面的後台


#### url

```javascript
https://[server_id]:8443/console
```

---

## monitor

用來觀察特定頻道的畫面

若開啟瀏覽器開發者介面的 console, 可以看到印出偵測到的人臉資料

#### url

```javascript
https://[server_id]:8443/monitor?ch=10
```

- `ch: Number` channelID

---


## store/enroll

商店應用的建檔

內建的 `/console` 建檔也會開啟這個頁面

#### url

```javascript
https://[server_id]:8443/store/enroll?ch=10&deviceIdx=0&mirrorFaceCam=0
```

- `ch: Number` channelID

- `deviceIdx: Number` 非必填. 預設 0. 當設備上有多個 webcam 時, 設定要用哪一個 webcam.

- `mirrorFaceCam: Number` 非必填. 預設 0. 決定是否要左右翻轉影像.

---

## store/checkout

商店應用的結帳

可以用 webcam 或掃描器或接收 gaziru 的回應, 來做到掃描商品功能.

#### url

```javascript
https://[server_id]:8443/store/checkout?ch=10&camType=webcam&scanCamIdx=0&faceCamIdx=0&mirrorFaceCam=0&faceTimeout=10000
```

- `ch: Number` channelID

- `camType: String` 非必填. 預設 webcam. 可用 webcam 或 ipcam. 決定影像來源.
 
- `scanCamIdx: Number` 非必填. 預設 0. 當設備上有多個 webcam 時, 設定要用哪一個 webcam. 這是掃條碼用的 cam.

- `faceCamIdx: Number` 非必填. 預設 0. 當設備上有多個 webcam 時, 設定要用哪一個 webcam. 這是掃臉用的 cam.

- `mirrorFaceCam: Number` 非必填. 預設 0. 決定是否要左右翻轉影像.

- `faceTimeout: Number` 非必填. 預設 10000. 決定過多久沒辨識結果, 就要回應為沒有建檔. 單位為 ms.

---

## store/member

商店應用的查詢

可以查詢餘額和模擬儲值

#### url

```javascript
https://[server_id]:8443/store/member?ch=10&camType=webcam&deviceIdx=0&mirrorFaceCam=0
```

- `ch: Number` channelID

- `camType: String` 非必填. 預設 webcam. 可用 webcam 或 ipcam. 決定影像來源.

- `deviceIdx: Number` 非必填. 預設 0. 當設備上有多個 webcam 時, 設定要用哪一個 webcam. 當 camType 為 webcam 時才有效.

- `mirrorFaceCam: Number` 非必填. 預設 0. 決定是否要左右翻轉影像.

---

