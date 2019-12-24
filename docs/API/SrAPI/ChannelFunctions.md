# Functions

---

## edit

修改 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md) 的任意資料

#### 範例

```
SrAPI.channel(channelID).edit(channelData);
```

- `channelID: Number`

- `channelData:` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

#### 回應

`修改後的` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## list

列出所有頻道及其所有資料

#### 範例

```
SrAPI.channel().list();
```

#### 回應

`Array of` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## getAll

取得特定頻道的所有資料

#### 範例

```
SrAPI.channel(channelID).getAll();
```
- `channelID: Number`

#### 回應

`此頻道的` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## getBaoFeng

取得特定頻道的金融區整合資料

#### 範例

```
SrAPI.channel(channelID).getBaoFeng();
```

- `channelID: Number`

#### 回應

```
{
    host: "",               // 目標 host
    port: 8888,             // 目標 port
    token: "",              // 驗證用的 token
    enabled: false
}
```

---

### getFA

取得特定頻道的 FA 資料

#### 範例

```
SrAPI.channel(channelID).getFA();
```

- `channelID: Number`

#### 回應

```
{
    host: "",               // 這是 sdb-nexus 本身的 IP, 因為是這裡當 server, 給 fa 丟資料進來.
    port: 8888,             // 承上, 這是開給 fa 連的 port.
    enabled: false
}
```

---

### getFR

取得特定頻道的對人臉辨識的 socket server 的連線資料

#### 範例

```
SrAPI.channel(channelID).getFR();
```

- `channelID: Number`

#### 回應

```
{
    host: "",               // socket server host
    port: 8888,             // socket server port
    threshold: [0.7, 0.7],  // 額外的門檻值, 通常都設成跟 socket server 上一樣即可.
    lingerMS: 500,          // 在這段時間內辨識到同一個人, 會被視為是同一次還在逗留, 不會觸發新的辨識結果.
    enrollStranger: false,  // 自動幫陌生人建檔. 
    enabled: false
}
```

---

### getFRSDBConn

取得特定頻道的對應 socket server 資料庫的資料

這會用於同步資料等情況

#### 範例

```
SrAPI.channel(channelID).getFRSDBConn();
```

- `channelID: Number`

#### 回應

```
{
    user: "",               
    password: "",
    server: "",
    database: "",
    enabled: false,
}
```

---

### getGaziru

取得特定頻道的對應 gaziru 的連線資料

在 gaziru 所在的機器, 需要有 gaziru-parser 負責當中介

#### 範例

```
SrAPI.channel(channelID).getGaziru();
```

- `channelID: Number`

#### 回應

```
{
    host: "",               // host
    port: 8787,             // gaziru-parser 開的 port, 目前固定是 8787.
    enabled: false
}
```

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
