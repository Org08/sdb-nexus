# Member

---

## add

新增 member

這只會新增在本地資料庫, 不會對臉辨引擎建檔

若想要直接建檔, 要使用 enroll 

> TODO: 連結到 enroll


#### 範例

```
SrAPI.member(channelID).add(MemberData)
```

- `channelID: Number`

- `MemberData:` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## edit

修改 member

這只會修改本地資料庫

#### 範例

```
SrAPI.member(channelID).edit(MemberData)
```

- `channelID: Number`

- `MemberData:` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`修改後的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## list

列出符合條件的 member

> TODO: 以下未修改

#### 範例

```
SrAPI.member(channelID).list({
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
