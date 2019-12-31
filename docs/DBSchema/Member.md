
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
