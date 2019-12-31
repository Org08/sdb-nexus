# PTS

## PTSData

PTS 的完整資料格式是 [PTSData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/PTSData.md)

## Functions

### getStats

取得 PTS 統計資料

只要同一個人在一小時內有新的追蹤資料, 就會納入同一次追蹤路徑

##### 範例

```javascript
SrAPI.pts(channelID).getStats({
    skip: 10,         // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查 
    limit: 20,
    inHours: 1,       
})
```

- `channelID: Number`

- `skip: Number` 略過幾筆. 預設 0.

- `limit: Number` 一次傳幾筆. 預設 20.

- `inHours: Number` 取得距目前時間前幾小時內的統計資料. 預設 1.

##### 回應

[PTSData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/PTSData.md)

---
