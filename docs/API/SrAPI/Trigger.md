# Trigger

直接觸發某些系統動作

可以當整合用的節點, 或是測試運作

## Functions

### baofeng

發送內建照片給金融區

##### 範例

```javascript
SrAPI.trigger(channelID).baofeng()
```

- `channelID: Number`

##### 回應

若發生錯誤, 會收到金融區回傳的 `body`

若運作正常, 只會收到 `undefined`

---

### frsDBSync

從臉辨引擎同步建檔資料至本系統

##### 範例

```javascript
SrAPI.trigger(channelID).frsDBSync({
    fromSeq: fromSeq
})
```

- `channelID: Number`

- `fromSeq: Number` 指定從目標 DB 中的哪個 Seq 開始撈. 最小值為 1. 非必填.


##### 回應

若發生錯誤, 會收到系統內部的錯誤訊息

若運作正常, 只會收到 `undefined`

---

### info

模擬接收到臉辨結果時, 轉傳給前端的動作

##### 範例

```javascript
SrAPI.trigger(channelID).info({
    MemberID: MemberID
})
```

- `channelID: Number`

- `MemberID: String` 非必填

##### 回應

若發生錯誤, 會收到系統內部的錯誤訊息

若未填 `MemberID`, 會發送內建固定資料

若填了 `MemerID`, 會查詢本地資料庫, 並發送該資料

若填了 `MemerID`, 但查不到, 會回應 `MEMBER_NOT_FOUND`


---

### udp

發送預先設定的資料

##### 範例

```javascript
SrAPI.trigger(channelID).udp()
```

- `channelID: Number`


##### 回應

若發生錯誤, 會收到 `[trigger][udp][e] ` 後面接錯誤訊息

若運作正常, 會收到 `[trigger][udp] ` 後面接送出的預設資料

---
