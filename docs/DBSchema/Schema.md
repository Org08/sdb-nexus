
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

同 FA, 是本地建立 SocketServer 接收來自 [gaziru-parser](https://github.com/Org08/sdb-nexus/blob/master/docs/Architecture/architecture.md#gaziru-parser) 的資料

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


# FARecord

## FARecordSchema

```javascript
{
    // NOTE: 前端輪播時根據 channelID 區分. 顯示的區域名稱則是 channelName.
    channelID: { type: Number, index: true, trim: true, required: [true, "no channelID"] },

    // NOTE: 因為 FA 每次重啟, 都會從頭編 humanId. 所以為了本地統計不要重複, 只要本地的 SocketServer 每次重新被 FA 連線, 就要隨機更新此 connId. (不知道 FA 重連是否是因為重啟, 所以反正重連就配新的)
    connId: { type: String, index: true, trim: true, required: [true, "no connId"] },
    humanId: { type: Number, index: true, required: [true, "no humanId"] },

    gender: { type: Number },                                 // -1:unknown, 0:female, 1:male

    age: { type: Number },                                    // -1, integer
    stayTime: { type: Number },                               //
    watchTime: { type: Number },                              //

    smileCount: { type: Number },                             //
    smile: { type: Number },                                  // -1:unknown, 0:no, 1:yes
    glasses: { type: Number },                                // -1:unknown, 0:no, 1:yes
    mask: { type: Number },                                   // -1:unknown, 0:no, 1:yes

    //
    status: { type: Number, index: true, default: 0 },
    updated: { type: Date, default: Date.now }
}
```

---


# FRRecord

## FRRecordSchema

```javascript
{
    event: { type: String, index: true, trim: true, required: [true, "no event"] },
    channelID: { type: Number, index: true, trim: true, required: [true, "no channelID"] },

    MemberID: { type: String, index: true, trim: true, required: [true, "no MemberID"] },
    MemberName: { type: String, index: true, trim: true, default: "" },
    Result: { type: Number, index: true, trim: true, default: 0 },                         
    Score: { type: Number, index: true, min: 0, max: 100, default: 0 },
    MatchImage: { type: String, default: "" },                                              // base64 string of the image

    group: { type: Number, default: 1 },

    //
    status: { type: Number, index: true, default: 1 },
    updated: { type: Date, default: Date.now }
}
```

---


# Member

## MemberSchema

```javascript
{
    event: { type: String, index: true, trim: true, required: [true, "no event"] },
    MemberID: { type: String, index: true, trim: true, required: [true, "no MemberID"] },

    MemberName: { type: String, index: true, trim: true, default: "" },
    refA: { type: String, trim: true, default: "" },
    refB: { type: String, trim: true, default: "" },
    refC: { type: String, trim: true, default: "" },
    Attribute_1: { type: String, trim: true, default: "" },
    Attribute_2: { type: String, trim: true, default: "" },
    Attribute_3: { type: String, trim: true, default: "" },
    Attribute_4: { type: String, trim: true, default: "" },
    Attribute_5: { type: String, trim: true, default: "" },

    //
    custom: { type: mongoose.Schema.Types.Mixed, default: {} },
    group: { type: Number, default: 1 },                            

    //
    image: { type: String, default: "" },                           // base64 string of the image

    //
    store: { type: StoreSchema, default: StoreSchema },
    info: { type: InfoSchema, default: InfoSchema },                // NOTE: 現在沒用到. 且 API 的 getInfo setInfo 指的是非子項目的基本資料.

    //
    status: { type: Number, index: true, default: 1 },
    updated: { type: Date, default: Date.now }
}
```

底下是子項目的細節

### StoreSchema

錢包和點數

```javascript
{
    balance: { type: Number, default: 1000 },
    point: { type: Number, default: 0 },
    pincode: { type: String, trim: true, default: "" }, // NOTE: 只是示意功能, 不應該明碼存. 商店應用全部都只是示意.
}
```

### InfoSchema

某些活動用到的欄位, showroom 可忽略

```javascript
{
    id: { type: String, index: true, trim: true, default: "" },
    name: { type: String, index: true, trim: true, default: "" },
    company: { type: String, index: true, trim: true, default: "" },
    title: { type: String, index: true, trim: true, default: "" },
    email: { type: String, index: true, trim: true, default: "" },
    phone: { type: String, index: true, trim: true, default: "" },
    remark: { type: String, default: "" },
}
```

---


# PTSRecord

## PTSRecordSchema

```javascript
{
    MemberID: { type: String, index: true, trim: true, required: [true, "no MemberID"] },
    MemberName: { type: String, index: true, trim: true },
    Image: { type: String },

    paths: [ mongoose.Schema.Types.Mixed ],
    zones: { type: mongoose.Schema.Types.Mixed },

    //
    status: { type: Number, index: true, default: 1 },
    updated: { type: Date, default: Date.now }
}
```

---


# StoreItem

## StoreItemSchema

```javascript
{
    event: { type: String, index: true, trim: true, required: [true, "no event"] },
    //
    code: { type: String, index: true, required: [true, "no code"] },
    name: { type: String, index: true, trim: true, default: "" },
    price: { type: Number, default: 100 },
    description: { type: String, default: "" },

    // ----

    status: { type: Number, index: true, default: 1 },
    updated: { type: Date, default: Date.now }
}
```

---


# SysLog

## SysLogSchema

```javascript
{
    channelID: { type: Number, index: true, default: 0 },
    flag: { type: String, index: true, trim: true },
    level: { type: String, index: true, trim: true },
    levelNum: { type: Number, index: true, default: 0 },
    msg: { type: String, default: "" },

    date: { type: Date, default: Date.now }
}
```

---


# User

目前本系統僅使用預設帳號, 也沒有明確劃分各功能權限

所以這個只會用於驗證預設帳號登入

## UserSchema

```javascript
{
    username: { type: String, index: true, trim: true, unique: true, required: [true, "no username"] },
    nickname: { type: String, index: true, trim: true, default: "----" },

    password: { type: String, trim: true },                             // after bcrypt

    group: { type: String, default: "customer" },                       // customer, staff, admin
    status: { type: Number, index: true, default: 0 },                  // -1:停用, 0:未啟用, 1:啟用
    updated: { type: Date, default: Date.now }
}
```

---
