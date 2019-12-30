# Monitor

---

## connect

連線指定頻道, 並根據設定接收資料

只需要呼叫一次, 並且無法更改設定值

#### 範例

```
SrAPI.monitor(channelID).connect({
    listen: {
        frame: true, 
        face: false, 
        member: false, 
        gaziru: false, 
        fa: false
    }
})
```

- `channelID: Number`

- `listen: Object`      設定要接收哪些資訊
  - `frame: Boolean`    單張畫面
  - `face: Boolean`     偵測到的人臉
  - `member: Boolean`   辨識到的 member
  - `gaziru: Boolean`   辨識到的商品
  - `fa: Boolean`       即時 fa 資料

---

## Events

### frame

```
SrAPI.monitor(channelID).on("frame", (data) => {

})
```

- `channelID: Number`

```
data = {
    base64Frame: base64Frame
}
```

- `base64Frame: String`


### face

```
SrAPI.monitor(channelID).on("face", (data) => {

})
```

- `channelID: Number`

```
face = {
    base64Face: base64Face,
    rect: { 
        x: x, 
        y: y, 
        width: width, 
        height: height 
    },
    date: date
}
```

- `base64Face: String`

- `rect: Object`
  - `x: Number`
  - `y: Number`
  - `width: Number`
  - `height: Number`

- `date: String`

### member

```
SrAPI.monitor(channelID).on("member", (MemberData) => {

})
```

- `MemberData:` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

### gaziru

```
SrAPI.monitor(channelID).on("gaziru", (StoreItemData) => {

})
```

- `StoreItemData:` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

### fa

```
SrAPI.monitor(channelID).on("fa", (FAData) => {

})
```

- `FAData:` [FAData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/FAData.md)

---
