# FA

---

## getStats

取得 FA 統計資料

#### 範例

```
SrAPI.fa(channelID).getStats({
    inSeconds: 3600,        // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查   
    pseudodata: {
        headCount: true,
        mask: true
    }
})
```

- `channelID: Number`

- `inSeconds: Number` 取得距目前時間前多少秒內的統計資料. 預設 3600.

- `pseudodata: Object` 設定為 true 的子項目, 會回傳模擬資料. 可以設的有 headCount, watchTime, age, smile, glasses, mask. 另外有個 all, 如果設了就會全部用模擬資料. 預設不使用模擬資料.


#### 回應

[FAData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/FAData.md)

---

## 即時資料

接收用來刷新前端介面的即時資料

[Monitor.on.fa](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Monitor.md#fa)

---
