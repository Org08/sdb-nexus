# Functions

---

## edit

修改 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md) 的任意資料

### 範例

```
SrAPI.channel(channelID).edit(channelData);
```

- `channelID: Number`

- `channelData:` [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

### 回應

修改後的 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## list

列出所有頻道及其所有資料

### 範例

```
SrAPI.channel().list();
```

#### 回應

Array of [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## getAll

取得特定頻道的所有資料

### 範例

```
SrAPI.channel(channelID).getAll();
```
- `channelID: Number`

### 回應

此頻道的 [ChannelData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/ChannelData.md)

---

## getBaoFeng

取得特定頻道的金融區整合資料

(這通常只有一個頻道被設定)

### 範例

```
SrAPI.channel(channelID).getBaoFeng();
```

- `channelID: Number`

### 回應

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
