
---

### setLog

修改設定檔 `./conf.json` 中的 log 資料

可以修改的欄位為 level 和 enabled

##### 範例

```javascript
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

##### 回應

```javascript
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
