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
    udp: {
        host: "",
        port: 8888,
        data: "",
        enabled: false
    },
    gaziru: {
        host: "",
        port: 8888,
        enabled: false
    },
    baofeng: {
        host: "",
        port: 8888,
        token: "",
        enabled: false
    },
    frsDBConn: {
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

### add

---

### edit

```
SrAPI.channel(1).edit({
    channelName: "",
    event: "",
    description: "",
    zone: "",
    custom: {},
    wsFeed: {
        host: "",
        port: 8888,
        enabled: false
    },
    fr: {
        host: "",
        port: 8888,
        threshold: [0.7, 0.7],
        lingerMS: 500,
        enrollStranger: false,
        enabled: false
    },
    fa: {
        host: "",
        port: 8888,
        enabled: false
    },
    tcp: {
        host: "",
        port: 8888,
        data: "",
        enabled: false
    },
    udp: {
        host: "",
        port: 8888,
        data: "",
        enabled: false
    },
    gaziru: {
        host: "",
        port: 8888,
        enabled: false
    },
    baofeng: {
        host: "",
        port: 8888,
        token: "",
        enabled: false
    },
    frsDBConn: {
        user: "",
        password: "",
        server: "",
        database: "",
        enabled: false,
    }
});

```


---

### del

---

### list

---

### getAll

---

### getBaoFeng

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
