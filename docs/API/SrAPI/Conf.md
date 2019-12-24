# Conf

---

## addProbe

設定要接收的系統資訊, 接收到的資訊會直接在 console 印出.

可以連續設定多種不同過濾條件, 所有設定過的條件都會印出.

#### 範例

```
SrAPI.channel().addProbe({
    flag: "sys",
    level: "info"
})
```

- `flag: String` sys, channel, member, store, storeItem, fa, fr, feed, gaziru, tcp, udp, frsdb, baofeng, frRecord, pts, trigger, conf, h264player

- `level: String` all, debug, info, warn, error, fatal

---

## clearProbe

清除要接收的系統資訊.

#### 範例

```
SrAPI.channel().clearProbe()
```

---

## getStore

取得設定檔 `./conf.json` 中的 store 資料.

目前僅用於設定 POS 介面的預設咖啡按鈕.

#### 範例

```
SrAPI.channel().getStore()
```

#### 回應

```
{
    coffee: {
        code: "coffee_0",
        name: "咖啡",
        price: 50
    }
}
```

---
