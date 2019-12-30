# Trigger

直接觸發某些系統動作

可以當整合用的節點, 或是測試運作

---

## baofeng

發送內建照片給金融區

#### 範例

```
SrAPI.trigger(channelID).baofeng()
```

- `channelID: Number`

#### 回應

若發生錯誤, 會收到金融區回傳的 body

若運作正常, 只會收到 undefined

---

## frsDBSync

從臉辨引擎同步建檔資料至本系統

#### 範例

```
SrAPI.trigger(channelID).frsDBSync({
    fromSeq: fromSeq
})
```

- `channelID: Number`

- `fromSeq: Number` 指定從目標 DB 中的哪個 Seq 開始撈. 最小值為 1. 非必填.


#### 回應

若發生錯誤, 會收到系統內部的錯誤訊息

若運作正常, 只會收到 undefined

---

## list

列出符合條件的 member

#### 範例

```
SrAPI.member(channelID).list({
    skip: 10,         // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查 
    limit: 20,
    MemberID: "",
    MemberName: "",
    group: 1
})
```

- `channelID: Number`

- `skip: Number` 略過幾筆. 預設 0.

- `limit: Number` 一次傳幾筆. 預設 20.

- `MemberID: String` 

- `MemberName: String` 

- `group: Number` -1: 陌生人, 0:黑名單, 1: 一般, 2: VIP, 3: 經銷商, 4: 客戶, 5: 員工

> NOTE: group 欄位目前沒有跟現場協調過, 這是之前合作時的定義

#### 回應

`Array of` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## enroll

新增 member, 且向辨識引擎建檔

#### 範例

```
SrAPI.member(channelID).enroll(MemberData)
```

- `channelID: Number`

- `MemberData: ` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

> MemberData.MemberID 和 MemberData.image 必填

#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## del

刪除 member

#### 範例

```
SrAPI.member(channelID).del({
    MemberID: ""
})
```

- `channelID: Number`

- `MemberID: String` 

#### 回應

`刪除的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

> 實際上是 MemberData.status 被改成 0

---
