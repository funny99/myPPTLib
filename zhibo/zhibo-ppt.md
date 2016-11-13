title: h5直播
speaker: gongjuan
url: 
transition: slide2
files: 
theme: moon

[slide]
# h5直播
## 龚娟

[slide]
# 相关知识点
----
* video
* HLS
* websocket

[slide]
# video
----
<p align="left">html5原生播放器 </p>
<p align="left">获取video对象其实就是获取video的dom节点</p> 
```
var video = document.getElementById('video');
```

[slide]
# video - 属性
----
```
video.error // null正常
video.error.code // 1用户终止 2网络错误 3解码错误 4URL无效
video.currentTime // 当前播放的位置，赋值可改变位置
video.duration // 当前资源长度，流返回无限
video.paused // 是否暂停（从视频页按home键回到主菜单或下拉通知栏，视频会自动暂停，恢复后会自动播放）
video.ended // 是否结束
video.autoPlay // 是否自动播放
...
```

[slide]
# video - 事件
----
```
loadstart // 客户端开始请求数据
error // 请求数据时遇到错误（可以通过上面的属性video.error.code查看具体错误原因）
play // 开始播放时触发
pause // 暂停时触发
loadeddata // 数据已加载
waiting // 等待数据，并非错误
playing // play触发后执行一次
canplaythrough // 可以播放，已加载好
timeupdate // 播放时间改变
durationchange // 资源长度改变
...
```

[slide]
# video - 坑点总结
----
* <p style="color:#FFFF33;">ios上会自动全屏，需要在video标签上设置一个属性<span style="color:red;">webkit-playsinline</span>，ios10及以上版本属性名改成<span style="color:red;">playsinline</span></p> {:&.bounceIn}
* <p style="color:#00FF00;">android上即使没设置属性controls，也会出现默认的播放按钮，这个是微信手Q内置浏览器处理的，需要依赖他们来解决</p>
* <p style="color:#FF9933;">android无法自动播放，调用video.play()也不行。必须用户执行touch操作才会触发</p>
* <p style="color:#FF6666;">video触发canplaythrough事件时，在ios上表示可以流畅播放了，playing表示开始播放。但在android上并不是，触发timeupdate事件后，而且video.currentTime不为0才表示已经开始播放</p>

[slide]
# HLS
---
* 全称为：HTTP Live Streaming，是一个基于http的视频流协议，由Apple公司实现，ios和高版本的android都支持。
* 使用很简单，video的src设置为一个m3u8的地址（http://7609.mpull.live.lecloud.com/live/11331/desc.m3u8）

[slide]
# HLS - 请求流程
----
1. http请求m3u8的url。 {:&.bounceIn}
2. 服务端返回一个m3u8的播放列表，这个播放列表是实时更新的，一般一次给出n段数据的url。
3. 客户端解析m3u8的播放列表，再按序请求每一段的url，获取ts数据流。

[slide]
* HLS - m3u8 
----
![hexo_mulu](/img/m3u8info.png)

[slide]
# HLS - 优缺点
---
* 优点
	* 跨平台，分享出去就可以直接观看 {:&.bounceIn}
	* 使用简单
* 缺点 
	* 延时较大。如果一个m3u8文件配置了5个ts文件，每个ts文件为6s，那么至少会延迟30s {:&.bounceIn}

[slide]
# websocket
----
<p align="left">客户端和服务端存在<span style="color:red;">持久</span>的链接，而且<span style="color:red;">双方</span>都可以随时开始发送数据</p>
<p align="left">主要用于直播中的聊天，上报及广播各种状态等</p>
```
websocket = new WebSocket(wsUri);
websocket.onopen = function(evt) {}; // 连接建立ok
websocket.onclose = function(evt) {}; // 连接关闭
websocket.onmessage = function(evt) { // 接收消息
	var obj = JSON.parse(evt.data); // 消息内容
};
websocket.onerror = function(evt) {}; // 出错

websocket.send(JSON.stringify(msgObj)); // 发送消息
```

[slide]
# 直播流程
----

[slide]
# 坑点总结
----
1. 微信手Q中通过unload、beforeunload事件无法监听到用户离开页面 {:&.bounceIn}
2. 微信中修改document.title无效
```
if(pageUtil.mobileSysType() == 'ios'){
    var $iframe = $('<iframe src="' + tplUtil.getImg(commonV.defaultCoverImg) + '" style="display:none;"></iframe>');
    $iframe.on('load', function(){
        setTimeout(function(){$iframe.off('load').remove();}, 0);
    }).appendTo(element.body);
}
```

[slide]
# 参考资料 
---- 
<http://www.xuanfengge.com/html5-video-play.html>  
<https://aotu.io/notes/2016/10/09/HTML5-SopCast/>  
<http://www.alloyteam.com/2016/05/h5-camera-literacy/>
<http://www.jianshu.com/p/404d01b8e713>

[slide]
## 谢谢

