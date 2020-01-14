
# Architecture

## Intro

由 `sdb-nexus` 和 `mongodb` 組成的主系統, 作為溝通其他功能節點的核心. 

後端有提供串流功能的 `sdb-feed` 和 偵測人臉的 `sdb-fd` 和 網頁服務的 `sdb-web`, 並整合人臉辨識的 `frs socket server` 和分析的 `fa` 和同步建檔資料的 `frs db`, 以及接收 `gaziru` 資料的 `gaziru-parser`, 還有串接通支金融區顯示的 `baofeng` 和接收閘門通知的 `web service`.

## 功能分類

- 核心
  - [sdb-nexus](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sdb-nexus.md)
  - [mongodb](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/mongodb.md)
- 子節點
  - [sdb-feed](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sub-nodes.md#sdb-feed)
  - [sdb-fd](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sub-nodes.md#sdb-fd)
  - [sdb-web](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/sub-nodes.md#sdb-web)
- 整合節點
  - [frs socket server](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/intergated-nodes.md#frs-socket-server)
  - [frs db](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/intergated-nodes.md#frs-db)
  - [fa](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/intergated-nodes.md#fa)
  - [gaziru-parser](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/intergated-nodes.md#gaziru-parser)
  - [baofeng](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/intergated-nodes.md#baofeng)


---

