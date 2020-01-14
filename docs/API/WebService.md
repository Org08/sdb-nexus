
# WebService

提供第三方整合介面


## URL

`http://[server_ip]:9527`


## Functions

### /trigger/info

觸發如同接收到辨識結果的動作

通常是第三方系統已經做完辨識, 但是要觸發本系統的後續動作時使用

##### 範例

```javascript
http://[server_ip]:9527/trigger/info?channelID=1&MemberID=AAA
```

- `channelID: Number` 要觸發的頻道

- `MemberID: String` 辨識到的 MemberID

---
