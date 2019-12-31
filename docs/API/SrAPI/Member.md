# Member

## MemberData

Member 的完整資料格式是 [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

## Functions

### add

新增 member

這只會新增在本地資料庫, 不會對臉辨引擎建檔

若想要直接建檔, 要使用 [enroll](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Member.md#enroll) 

#### 範例

```javascript
SrAPI.member(channelID).add(MemberData)
```

- `channelID: Number`

- `MemberData:` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

### edit

修改 member

這只會修改本地資料庫

#### 範例

```javascript
SrAPI.member(channelID).edit(MemberData)
```

- `channelID: Number`

- `MemberData:` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`修改後的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

### list

列出符合條件的 member

#### 範例

```javascript
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

### enroll

新增 member, 且向辨識引擎建檔

#### 範例

```javascript
SrAPI.member(channelID).enroll(MemberData)
```

- `channelID: Number`

- `MemberData: ` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

> MemberData.MemberID 和 MemberData.image 必填

#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

### del

刪除 member

#### 範例

```javascript
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
