# 百度网盘工具集
---
## 1 百度网盘
### 1.1 百度网盘视频在线倍速播放
>**注**：本内容来自CSDN博主，[点击](https://blog.csdn.net/weijifen000/article/details/79889247)阅读原文。
- 浏览器F12进入开发者模式选择`Console`输入以下代码即可实现加速；
  - 百度网盘视频在线1.5倍速播放核心代码;
    ```JS
    videojs.getPlayers("video-player").html5player.tech_.setPlaybackRate(1.5)
    ```
  - 百度网盘视频在线任意倍率播放设置；
    ```JS
    videojs.getPlayers("video-player").html5player.tech_.setPlaybackRate(任意倍率)
    ```