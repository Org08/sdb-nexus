# Channel

所有的應用都是基於 Channel

每個 Channel 可以獨立設定不同的功能

## ChannelData

所有的 Channel 的核心資料都是 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

## Functions

### edit

修改 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md) 的任意資料

#### 範例

```javascript
SrAPI.channel(channelID).edit(channelData)
```

- `channelID: Number`

- `channelData:` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

#### 回應

`修改後的` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

### list

列出所有頻道及其所有資料

#### 範例

```javascript
SrAPI.channel().list()
```

#### 回應

`Array of` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

### getAll

取得特定頻道的所有資料

#### 範例

```javascript
SrAPI.channel(channelID).getAll()
```
- `channelID: Number`

#### 回應

`此頻道的` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

### getBaoFeng

取得特定頻道的金融區整合資料

#### 範例

```javascript
SrAPI.channel(channelID).getBaoFeng()
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

```javascript
SrAPI.channel(channelID).getFA()
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

```javascript
SrAPI.channel(channelID).getFR()
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

```javascript
SrAPI.channel(channelID).getFRSDBConn()
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

```javascript
SrAPI.channel(channelID).getGaziru()
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

取得特定頻道的基本資料

#### 範例

```javascript
SrAPI.channel(channelID).getInfo()
```

- `channelID: Number`

#### 回應

```
{
    channelName: "",            // 只是個名字.
    event: "",                  // 當需要讓不同 channel 給不同活動使用, 可用這個來區隔.
    description: "",            // 只是個描述.
    zone: "",                   // 追蹤功能會根據此值來分區.
    custom: {},                 // 可以隨便塞東西的通用欄位. 當向 FRS 直接同步資料, 會把整包都備份在這.
}
```

---

### getTCP

取得特定頻道觸發 TCP 指令的資料 (未實裝)

#### 範例

```javascript
SrAPI.channel(channelID).getTCP()
```

- `channelID: Number`

#### 回應

```
{
    host: "",
    port: 8888,
    data: "",
    enabled: false
}
```

---

### getUDP

取得特定頻道觸發 UDP 指令的資料

#### 範例

```javascript
SrAPI.channel(channelID).getUDP()
```

- `channelID: Number`

#### 回應

```
{
    host: "",               // 目標 host
    port: 8888,             // 目標 port
    data: "",               // 空白隔開的十六進位字串, 例如 "0A 3B 45". 辨識成功時發出.
    enabled: false
}
```

---

### getWSFeed

取得特定頻道影像來源的連線資料

> TODO: 連到 sdb-feed 章節

#### 範例

```javascript
SrAPI.channel(channelID).getWSFeed()
```

- `channelID: Number`

#### 回應

```
{
    host: "",
    port: 8888,
    enabled: false
}
```

---

### setBaoFeng

設定特定頻道的金融區整合資料

#### 範例

```javascript
SrAPI.channel(channelID).setBaoFeng({ 
    host: "",       // 這些參數至少傳一個即可, 不強制都傳
    port: 8888,
    token: "",
    enabled: false
})
```

- `channelID: Number`

- `host: String` 目標 host

- `port: Number` 目標 port

- `token: String` 驗證用的 token

- `enabled: Boolean`


#### 回應

```
{
    host: "",
    port: 8888,
    token: "",
    enabled: false
}
```

---

### setFA

設定特定頻道的 FA 資料

#### 範例

```javascript
SrAPI.channel(channelID).setFA({ 
    host: "",       // 這些參數至少傳一個即可, 不強制都傳
    port: 8888,
    enabled: false
})
```

- `channelID: Number`

- `host: String` 這是 sdb-nexus 本身的 IP, 因為是這裡當 server, 給 fa 丟資料進來.

- `port: Number` 承上, 這是開給 fa 連的 port.

- `enabled: Boolean`


#### 回應

```
{
    host: "",
    port: 8888,
    enabled: false
}
```

---

### setFR

設定特定頻道的對人臉辨識的 socket server 的連線資料

#### 範例

```javascript
SrAPI.channel(channelID).setFA({ 
    host: "",               // 這些參數至少傳一個即可, 不強制都傳
    port: 8888,             
    threshold: [0.7, 0.7],  
    lingerMS: 500,          
    enrollStranger: false,  
    enabled: false
})
```

- `channelID: Number`

- `host: String` socket server host

- `port: Number` socket server port

- `threshold: [Number]` 額外的門檻值, 通常都設成跟 socket server 上一樣即可.

- `lingerMS: Number` 在這段時間內辨識到同一個人, 會被視為是同一次還在逗留, 不會觸發新的辨識結果.

- `enrollStranger: Boolean` 自動幫陌生人建檔. 

- `enabled: Boolean`


#### 回應

```
{
    host: "",              
    port: 8888,            
    threshold: [0.7, 0.7], 
    lingerMS: 500,         
    enrollStranger: false, 
    enabled: false
}
```

---

### setFRSDBConn

設定特定頻道的對應 socket server 資料庫的資料

這會用於同步資料等情況

#### 範例

```javascript
SrAPI.channel(channelID).setFRSDBConn({ 
    user: "",          // 這些參數至少傳一個即可, 不強制都傳     
    password: "",
    server: "",
    database: "",
    enabled: false,
})
```

- `channelID: Number`

- `user: String` db user

- `password: String` db password

- `server: String` db url

- `database: Number` db name

- `enabled: Boolean`


#### 回應

```
{
    user: "aaaa",               
    password: "bbbb",
    server: "1.1.1.1",
    database: "DBDBDB",
    enabled: false,
}
```

---

### setGaziru

設定特定頻道的對應 gaziru 的連線資料

在 gaziru 所在的機器, 需要有 gaziru-parser 負責當中介

#### 範例

```javascript
SrAPI.channel(channelID).setGaziru({ 
    host: "",          // 這些參數至少傳一個即可, 不強制都傳     
    port: "",
    enabled: false,
})
```

- `channelID: Number`

- `host: String` host

- `port: Number` gaziru-parser 開的 port, 目前固定是 8787.

- `enabled: Boolean`


#### 回應

```
{
    host: "", 
    port: 8787,
    enabled: false
}
```

---

### setInfo

設定特定頻道的基本資料

#### 範例

```javascript
SrAPI.channel(channelID).setInfo({
    channelName: "",        // 這些參數至少傳一個即可, 不強制都傳     
    event: "", 
    description: "", 
    zone: "",
    custom: {},
    enabled: false,
})
```

- `channelID: Number`

- `channelName: String` 只是個名字.

- `event: String` 當需要讓不同 channel 給不同活動使用, 可用這個來區隔.

- `description: String` 只是個描述.

- `zone: String` 追蹤功能會根據此值來分區.

- `custom: Object` 可以隨便塞東西的通用欄位. 當向 FRS 直接同步資料, 會把整包都備份在這.

- `enabled: Boolean`


#### 回應

```
{
    channelName: "", 
    event: "", 
    description: "", 
    zone: "",
    custom: {}
}
```


---

### setTCP

設定特定頻道觸發 TCP 指令的資料 (未實裝)

#### 範例

```javascript
SrAPI.channel(channelID).setTCP({
    host: "",           // 這些參數至少傳一個即可, 不強制都傳  
    port: 8888,
    data: "",
    enabled: false
})
```

- `channelID: Number`

- `host: String`

- `port: Number`

- `data: String`

- `enabled: Boolean`


#### 回應

```
{
    host: "",
    port: 8888,
    data: "",
    enabled: false
}
```


---

### setUDP

設定特定頻道觸發 UDP 指令的資料

#### 範例

```javascript
SrAPI.channel(channelID).setUDP({
    host: "",           // 這些參數至少傳一個即可, 不強制都傳  
    port: 8888,
    data: "",
    enabled: false
})
```

- `channelID: Number`

- `host: String` 目標 host.

- `port: Number` 目標 port.

- `data: String` 空白隔開的十六進位字串, 例如 "0A 3B 45". 辨識成功時發出.

- `enabled: Boolean`


#### 回應

```
{
    host: "",
    port: 8888,
    data: "",
    enabled: false
}
```

---

### setWSFeed

設定特定頻道影像來源的連線資料

> TODO: 連到 sdb-feed 章節

#### 範例

```javascript
SrAPI.channel(channelID).setWSFeed({
    host: "",           // 這些參數至少傳一個即可, 不強制都傳  
    port: 8888,
    enabled: false
})
```

- `channelID: Number`

- `host: String`

- `port: Number`

- `enabled: Boolean`


#### 回應

```
{
    host: "",
    port: 8888,
    enabled: false
}
```

---
