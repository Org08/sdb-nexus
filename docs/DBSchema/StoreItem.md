
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
