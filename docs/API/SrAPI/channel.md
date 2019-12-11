# Channel

## Intro

每個 channel 都是由以下資料組成, 用來控制其具備的功能

```
ChannelData = {
    channelName: "",            // 只是個名字
    event: "",                  // 當需要讓不同 channel 給不同活動使用, 可用這個來區隔.
    description: "",            // 只是個描述
    zone: "",                   // 追蹤功能會根據此值來分區
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
