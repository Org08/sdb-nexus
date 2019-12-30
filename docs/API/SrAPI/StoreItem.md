# StoreItem

> 目前商品會綁定在建立時的那個 channel, 其他 channel 會搜尋不到. 若這會造成困擾, 之後可以改成共通.

---

## add

新增商品

#### 範例

```
SrAPI.storeItem(channelID).add({
    code: code,
    name: name,
    price: price,
    description: description
})
```

- `channelID: Number`

- `code: String` 商品的 Barcode

- `name: String` 商品名稱

- `price: Number` 商品價錢

- `description: String` 商品描述. 非必填.


#### 回應

```
{
    code: "AAAAAAAAAAA",
    name: "AAA",
    price: 100,
    description: ""
}
```

---

## edit

修改商品

#### 範例

```
SrAPI.storeItem(channelID).edit({
    code: code,
    name: name,
    price: price,
    description: description
})
```

- `channelID: Number`

- `code: String` 商品的 Barcode. 在此處為搜尋條件, 不會被修改.

- `name: String` 商品名稱

- `price: Number` 商品價錢

- `description: String` 商品描述. 非必填.


#### 回應

```
{
    code: "AAAAAAAAAAA",
    name: "AAA",
    price: 100,
    description: ""
}
```

---

## list

列出符合條件的 member

#### 範例

```
SrAPI.member(channelID).list({
    skip: 10,         // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查 
    limit: 20,
    MemberID: "",
    MemberName: "",
    group: 1
})
```

- `channelID: Number`

- `skip: Number` 略過幾筆. 預設 0.

- `limit: Number` 一次傳幾筆. 預設 20.

- `MemberID: String` 

- `MemberName: String` 

- `group: Number` -1: 陌生人, 0:黑名單, 1: 一般, 2: VIP, 3: 經銷商, 4: 客戶, 5: 員工

> NOTE: group 欄位目前沒有跟現場協調過, 這是之前合作時的定義

#### 回應

`Array of` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## enroll

新增 member, 且向辨識引擎建檔

#### 範例

```
SrAPI.member(channelID).enroll(MemberData)
```

- `channelID: Number`

- `MemberData: ` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

> MemberData.MemberID 和 MemberData.image 必填

#### 回應

`新增的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

---

## del

刪除 member

#### 範例

```
SrAPI.member(channelID).del({
    MemberID: ""
})
```

- `channelID: Number`

- `MemberID: String` 

#### 回應

`刪除的` [MemberData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/MemberData.md)

> 實際上是 MemberData.status 被改成 0

---
