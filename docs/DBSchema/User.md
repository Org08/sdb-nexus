
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
