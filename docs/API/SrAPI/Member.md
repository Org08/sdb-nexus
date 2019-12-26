# Member

---

## add

新增 [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

這只會新增在本地資料庫, 不會對臉辨引擎建檔

若想要直接建檔, 要使用 enroll 

> TODO: 連結到 enroll


#### 範例

```
SrAPI.member(channelID).add(MemberData)
```

- `channelID: Number`

- `MemberData: ` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## edit

修改 [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

這只會修改本地資料庫

#### 範例

```
SrAPI.member(channelID).edit(MemberData)
```

- `channelID: Number`

- `MemberData: ` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)


#### 回應

`修改後的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---
