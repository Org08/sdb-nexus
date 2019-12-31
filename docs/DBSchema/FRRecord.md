
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
