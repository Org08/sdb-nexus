
# StoreItemData

每個 storeItem 都是由以下資料組成

```javascript
StoreItemData = {
    event: "",              // 當需要讓不同 channel 給不同活動使用, 可用這個來區隔. 這會自動根據操作時的 channel 設定, 不需要額外設.
    
    //
    code: "",               // 商品 Barcode
    name: "",               //
    price: 100,             //
    description: "",        //

}
```
