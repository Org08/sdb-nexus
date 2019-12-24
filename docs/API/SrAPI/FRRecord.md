# FRRecord

---

## list

列出人臉辨識紀錄

#### 範例

```
SrAPI.frRecord(channelID).list({
    skip: 10,         // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查 
    limit: 20,
    MemberID: "",
    MemberName: "",
    Result: 1, 
    Score: 70,
    group: 1
})
```

- `channelID: Number`

- `skip: Number` 略過幾筆. 預設 0.

- `limit: Number` 一次傳幾筆. 預設 20.

- `MemberID: String` 

- `MemberName: String` 

- `Result: Number` 0, 1

- `Score: Number` 0-100 (範圍視 frs 版本而定, 有的是 0-1)

- `group: Number` -1: 陌生人, 0:黑名單, 1: 一般, 2: VIP, 3: 經銷商, 4: 客戶, 5: 員工

> NOTE: group 欄位目前沒有跟現場協調過, 這是之前合作時的定義

#### 回應

```
[{
    MemberName: "",
    Result: 1
    Score: 0.6694,
    MatchImage: "", // base64 string
    group: 1,
    status: 1,
    event: "",
    channelID: 10,
    MemberID: ""
    updated: "2019-12-13T03:21:47.206Z"
},
...
]
```

---
