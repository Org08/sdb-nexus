# PTS

---

## getStats

取得 PTS 統計資料

只要同一個人在一小時內有新的追蹤資料, 就會納入同一次追蹤路徑

#### 範例

```
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

#### 回應

```
{
    MemberID: MemberID,
    MemberName: MemberName,
    Image: "",              // base64 string
    paths: [ path ],        // 依時間序排列
    zones: zones            // 各區停留時間
}

// 以下是各組資料細節

path = {
    channelID: channelID,
    zone: "A",
    date: ""
}

zones = { // 有出現過的 zone 才會有值, 單位是 ms
    A: 0,
    B: 0,
}

```

---

## 即時資料

接收用來刷新前端介面的即時資料

> TODO: 連結到 monitor 收即時資料的章節
