# Channel

## Intro

每個 channel 都是由以下資料組成, 用來控制其具備的功能

```
ChannelData = {
    channelName: "",            // 只是個名字.
    event: "",                  // 當需要讓不同 channel 給不同活動使用, 可用這個來區隔.
    description: "",            // 只是個描述.
    zone: "",                   // 追蹤功能會根據此值來分區.
    custom: {},                 // 可以隨便塞東西的通用欄位. 當向 FRS 直接同步資料, 會把整包都備份在這.
    wsFeed: {                   // 頻道的影像來源. 包含整個畫面與單張臉與即時串流. 詳見 sdb-feed.
        host: "",
        port: 8888,
        enabled: false
    },
    fr: {                       // FRS
        host: "",               // socket server host
        port: 8888,             // socket server port
        threshold: [0.7, 0.7],  // 額外的門檻值, 通常都設成跟 socket server 上一樣即可.
        lingerMS: 500,          // 在這段時間內辨識到同一個人, 會被視為是同一次還在逗留, 不會觸發新的辨識結果.
        enrollStranger: false,  // 自動幫陌生人建檔. 
        enabled: false
    },
    fa: {                       // FA
        host: "",               // 這是 sdb-nexus 本身的 IP, 因為是這裡當 server, 給 fa 丟資料進來.
        port: 8888,             // 承上, 這是開給 fa 連的 port.
        enabled: false
    },
    tcp: {                      // TCP (未實裝)
        host: "",
        port: 8888,
        data: "",
        enabled: false
    },
    udp: {                      // UDP 
        host: "",               // 目標 host
        port: 8888,             // 目標 port
        data: "",               // 空白隔開的十六進位字串, 例如 "0A 3B 45". 辨識成功時發出.
        enabled: false
    },
    gaziru: {                   // Gaziru (在 gaziru 所在的機器上, 需要裝 gaziru-parser 來負責溝通)
        host: "",               // host
        port: 8787,             // gaziru-parser 開的 port, 目前固定是 8787.
        enabled: false
    },
    baofeng: {                  // BaoFeng (丟臉給金融區)
        host: "",               // 目標 host
        port: 8888,             // 目標 port
        token: "",              // 驗證用的 token
        enabled: false
    },
    frsDBConn: {                // FRS DB (同步 member)
        user: "",               
        password: "",
        server: "",
        database: "",
        enabled: false,
    }
}
```



## functions

---

### edit

修改 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/channel.md#intro) 的任意資料

- `channelID: Number`

- `channelData:` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/channel.md#intro)

範例

```
SrAPI.channel(channelID).edit(channelData);
```

---

### list

列出所有頻道及其所有資料

範例

```
SrAPI.channel().list();
```

---

### getAll

取得特定頻道的所有資料

- `channelID: Number`

範例

```
SrAPI.channel(channelID).getAll();
```

---

### getBaoFeng

取得特定頻道的金融區整合資料

(這通常只有一個頻道被設定)

- `channelID: Number`

範例

```
SrAPI.channel(channelID).getBaoFeng();
```

---

### getFA

---

### getFR

---

### getFRSDBConn

---

### getGaziru

---

### getInfo

---

### getTCP

---

### getUDP

---

### getWSFeed

---

### setBaoFeng

---

### setFA

---

### setFR

---

### setFRSDBConn

---

### setGaziru

---

### setInfo

---

### setTCP

---

### setUDP

---

### setWSFeed

---
