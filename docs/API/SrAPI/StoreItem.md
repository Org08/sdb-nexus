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

`新增的` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

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

`修改的` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

---

## list

列出符合條件的商品

#### 範例

```
SrAPI.storeItem(channelID).list({
    skip: 10,         // 這些全都是選擇性參數, 若都不下, 就只會用預設條件查 
    limit: 20,
})
```

- `channelID: Number`

- `skip: Number` 略過幾筆. 預設 0.

- `limit: Number` 一次傳幾筆. 預設 20.


#### 回應

`Array of` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

---

## find

查詢單個 barcode

通常用於掃描條碼後的查詢

#### 範例

```
SrAPI.storeItem(channelID).find({
    code: code
})
```

- `channelID: Number`

- `code: String` 商品的 Barcode

#### 回應

`查到的` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

---

## del

刪除商品

#### 範例

```
SrAPI.storeItem(channelID).del({
    code: code
})
```

- `channelID: Number`

- `code: String` 商品的 Barcode

#### 回應

`刪除的` [StoreItemData](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/StoreItemData.md)

> 實際上是 StoreItemData.status 被改成 0

---
