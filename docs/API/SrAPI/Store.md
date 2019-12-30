# Store

> 這只是模擬流程, 請不要拿去做真的結帳. 例如 checkout 沒有驗證, 只要給數字都會照扣.

---

## checkout

結帳

#### 範例

```
SrAPI.store(channelID).checkout({
     MemberID: "AAAA",
     total: 100
})
```

- `channelID: Number`

- `MemberID: String`

- `total: Number` 本次結帳要扣帳戶多少錢


#### 回應

```
{
    MemberID: "AAAA",
    MemberName: "AAAA",
    store: {
        balance: 900,
        point: 0
    }
}

```

---

## recharge

儲值

目前固定呼叫一次會儲 100

#### 範例

```
SrAPI.store(channelID).recharge({
     MemberID: "AAAA"
})
```

- `channelID: Number`

- `MemberID: String`

#### 回應

```
{
    MemberID: "AAAA",
    MemberName: "AAAA",
    store: {
        balance: 1000,
        point: 0
    }
}

```

---

