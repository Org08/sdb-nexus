
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
