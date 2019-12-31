
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
