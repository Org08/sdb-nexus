
# MemberData

每個 member 都是由以下資料組成

為了整合多種版本的臉辨引擎, 有些欄位只會在特定版本用到

```
MemberData = {
    event: ",             // 當需要讓不同 channel 給不同活動使用, 可用這個來區隔. 這會自動根據操作時的 channel 設定, 不需要額外設.
    MemberID: "",         //

    //
    MemberName: "",
    refA: "",
    refB: "",
    refC: "",
    Attribute_1: "",
    Attribute_2: "",
    Attribute_3: "",
    Attribute_4: "",
    Attribute_5: "",

    //
    custom: {},           // 可以任意塞資料. 當與臉辨引擎的資料庫同步時, 會把原始資料儲存在這. 
    group: 1,             // -1: 陌生人, 0:黑名單, 1: 一般, 2: VIP, 3: 經銷商, 4: 客戶, 5: 員工 (目前沒有跟現場協調過, 這是之前合作時的定義)

    //
    image: ""             // base64 string of the image

    //
    store: {              // POS 結帳相關功能
        balance: 1000,    // 餘額, 預設值為 1000.
        point: 0,         // 集點, 目前前端沒用到.
        pincode: "",      // 結帳密碼, 目前前端沒用到
    },
    
    //
    info: {               // 某些版本的自定義欄位, 將棄用, 會以 custom 取代. 注意: 這不是前端 API 的 info.
        id: "",
        name: "",
        company: "",
        title: "",
        email: "",
        phone: "",
        remark: ""    
    }
    
}
```
