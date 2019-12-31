
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
