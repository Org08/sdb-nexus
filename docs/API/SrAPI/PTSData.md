
# PTSData

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
