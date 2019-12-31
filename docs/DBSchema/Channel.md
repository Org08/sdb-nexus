
# Channel

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

    // 寶豐, showroom 金融區, post 資料過去
    baofeng: { type: BaoFengSchema, default: BaoFengSchema },

    // FRS 資料庫
    frsDBConn: { type: FRSDBConnSchema, default: FRSDBConnSchema },

    // ----

    status: { type: Number, default: 1 },
    updated: { type: Date, default: Date.now }
}
```
