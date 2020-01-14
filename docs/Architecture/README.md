
# Architecture

## Intro

由 `sdb-nexus` 和 `mongodb` 組成的主系統, 作為溝通其他功能節點的核心. 

後端有提供串流功能的 `sdb-feed` 和 偵測人臉的 `sdb-fd` 和 網頁服務的 `sdb-web`, 並整合人臉辨識的 `frs socket server` 和分析的 `fa` 和同步建檔資料的 `frs db`, 以及接收 `gaziru` 資料的 `gaziru-parser`, 還有串接通支金融區顯示的 `baofeng` 和接收閘門通知的 `web service`.

前端則提供設定用的 `console`, 模擬商店系列功能的 `store`, 方便確認運作的 `monitor`, 還有純文字的後台控制與開發測試介面 `api`. 另外還有各種客製介面.


---

