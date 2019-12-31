
# Channel

## ChannelSchema

```javascript
{
    //
    channelID: { type: Number, index: true, required: [true, "no channelID"] },
    channelName: { type: String, index: true, trim: true, default: "" },
    event: { type: String, index: true, trim: true, default: "" },  
    description: { type: String, default: "" },
    zone: { type: String, index: true, trim: true, default: "" },

    custom: { type: mongoose.Schema.Types.Mixed, default: {} },

    // feed
    wsFeed: { type: WSFeedSchema, default: WSFeedSchema },

    // face recognition
    fr: { type: FRSchema, default: FRSchema },

    // face analysis
    fa: { type: FASchema, default: FASchema },

    // tcp socket (未實作)
    tcp: { type: TCPSchema, default: TCPSchema },

    // udp socket
    udp: { type: UDPSchema, default: UDPSchema },

    // gaziru
    gaziru: { type: GaziruSchema, default: GaziruSchema },

    // 金融區, post 資料過去
    baofeng: { type: BaoFengSchema, default: BaoFengSchema },

    // FRS 資料庫
    frsDBConn: { type: FRSDBConnSchema, default: FRSDBConnSchema },

    // ----

    status: { type: Number, default: 1 },
    updated: { type: Date, default: Date.now }
}
```

底下是子項目的細節

### WSFeedSchema

與影像來源及臉部偵測來源的連線資訊

```javascript
{
    host: { type: String, trim: true, default: "" },
    port: { type: Number, min:0, max: 65535, default: 9001 },
    enabled: { type: Boolean, default: false },  
}
```

### FRSchema

與 SocketServer 的連線資訊

以及辨識功能的相關參數

```javascript
{
    host: { type: String, trim: true, default: "" },                // 通常是 IP
    port: { type: Number, min:0, max: 65535, default: 13005 },      //
    threshold: { type: [Number], default: [0.7, 0.7] },             // 分數門檻. 低於下限算失敗. 高於上限算成功. 兩者之間視為需要人工檢查. (當兩個設一樣, 就是不用人工檢查機制)
    lingerMS: { type: Number, default: 500 },                       // 在此時間內重複辨識到的人, 視為逗留中, 不會發出辨識結果

    enabled: { type: Boolean, default: false },                     //
    enrollStranger: { type: Boolean, default: false },              // 將陌生人建檔
}
```

### FASchema

FA 的情況跟 FR 相反, FA 需要本系統開 SocketServer, 所以此處設定的是本地 SocketServer 的 host 與 port

```javascript
{
    host: { type: String, trim: true, default: "" },                // 通常是 IP
    port: { type: Number, min:0, max: 65535, default: 13006 },      //
    enabled: { type: Boolean, default: false },                     //
}
```

### TCPSchema

辨識成功後所觸發的 TCP 訊息

```javascript
{
    host: { type: String, trim: true, default: "" },                // 通常是 IP
    port: { type: Number, min:0, max: 65535, default: 4001 },       //
    enabled: { type: Boolean, default: false },                     //
    data: { type: String, trim: true, default: "" },
}
```

### UDPSchema

辨識成功後所觸發的 UDO 訊息

```javascript
{
    host: { type: String, trim: true, default: "" },                // 通常是 IP
    port: { type: Number, min:0, max: 65535, default: 4001 },       //
    enabled: { type: Boolean, default: false },                     //
    data: { type: String, trim: true, default: "" },
}
```

### GaziruSchema

同 FA, 是本地建立 SocketServer 接收來自 gaziru-parser 的資料

> TODO: 連結到 gaziru-parser

```javascript
{
    host: { type: String, trim: true, default: "" },                // 通常是 IP
    port: { type: Number, min:0, max: 65535, default: 8787 },       //
    enabled: { type: Boolean, default: false },                     //
}
```

### BaoFengSchema

post 資料去金融區用的連線資訊

```javascript
{
    host: { type: String, trim: true, default: "" },                //
    port: { type: Number, min:0, max: 65535, default: 80 },         //
    token: { type: String, trim: true, default: "" },               //
    enabled: { type: Boolean, default: false },                     //
}
```

### FRSDBConnSchema

與辨識引擎的資料庫的連線資訊

```javascript
{
    user: { type: String, trim: true, default: "" },
    password: { type: String, trim: true, default: "" },
    server: { type: String, trim: true, default: "" },
    database: { type: String, trim: true, default: "" },
    enabled: { type: Boolean, default: false },
}
```

---
