# Conf

---

## addProbe

設定要接收的系統資訊, 接收到的資訊會直接在 console 印出.

可以連續設定多種不同過濾條件, 所有設定過的條件都會印出.

> TODO: 少寫了指定 channelID

#### 範例

```
SrAPI.conf().addProbe({
    flag: "sys",
    level: "info",
    channelID: 1
})
```

- `flag: String` sys, channel, member, store, storeItem, fa, fr, feed, gaziru, tcp, udp, frsdb, baofeng, frRecord, pts, trigger, conf, h264player

- `level: String` all, debug, info, warn, error, fatal

- `channelID: Number` 除了 sys 以外, 其他都可用 channelID 區隔

---

## clearProbe

清除要接收的系統資訊.

#### 範例

```
SrAPI.conf().clearProbe()
```

---

## getStore

取得設定檔 `./conf.json` 中的 store 資料.

目前僅用於設定 POS 介面的預設咖啡按鈕.

#### 範例

```
SrAPI.conf().getStore()
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

## setLog

修改設定檔 `./conf.json` 中的 log 資料.

可以修改的欄位為 level 和 enabled.

#### 範例

```
SrAPI.conf().setLog({    // 設定值都不是必填
    sys: {
        level: "debug"
    },
    channel: {
        enabled: false
    },
    member: {
        level: "info",
        enabled: true
    }
})
```

#### 回應

```
{
    sys: {
        level: "info",
        enabled: true
    },
    channel: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    member: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    store: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    storeItem: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    fa: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    fr: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    feed: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    gaziru: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    tcp: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    udp: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    frsdb: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    baofeng: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    frRecord: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    pts: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    trigger: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    conf: {
        level: "info",
        enabled: true,
        channelCnt: 20
    },
    h264player: {
        level: "info",
        enabled: true,
        channelCnt: 20
    }
}
```

---
