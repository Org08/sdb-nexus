# H264Player

前端播放 H264 影像所需的控制

## Functions

### getUrl

取得前端播放器所需的 url

必須是有設定 [wsFeed](https://github.com/Org08/sdb-nexus/blob/master/docs/API/SrAPI/Channel.md#setWSFeed) 的頻道才能使用

除了整合在前端播放器裡, 其他地方通常用不到

##### 範例

```javascript
SrAPI.h264Player(channelID).getUrl()
```

- `channelID: Number`

---
