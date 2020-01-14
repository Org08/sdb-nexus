
# Intergrated-Nodes

整合進來的各種關鍵功能節點

可以跟主系統在同樣的機器執行, 也可以視需要分散配置

---

## frs socket server 

臉辨服務

可以在 channel 的 [setFR](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#setFR) 與 [getFR](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#getFR) 進行設定

不同 channel 可以對應不同 socket server

---

## frs db

臉辨服務的資料庫

主要用於同步建檔資料

可以在 channel 的 [setfrsdbconn](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#setfrsdbconn) 與 [getfrsdbconn](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#getfrsdbconn) 進行設定

目前同步功能限於 channel 1 使用

---

## fa

性別年齡等分析服務

不同於大部分的整合, 這個是 [sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-nexus.md) 開 socket 給 fa 連線丟資料

可以在 channel 的 [setFA](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#setFA) 與 [getFA](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#getFA) 進行設定

---

## gaziru-parser

與 gaziru 溝通用的程式

- 此程式目前必須被直接置於 `gaziru` 資料夾中

- 啟動後會自動執行 `gaziru` 資料夾中的 `run_1920x1080_run_local.bat`

- parse 輸出的結果, 把 HIT 送給主系統 [sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-nexus.md)

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

## baofeng

金融區整合設定

在有啟用的頻道, 當有辨識結果時, 會根據此設定把資料發送出去

可以在 channel 的 [setBaoFeng](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#setBaoFeng) 與 [getBaoFeng](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#getBaoFeng) 進行設定

---
