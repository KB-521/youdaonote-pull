他们的控件属性大体相同，可以动态创建视音频；



控件属性：

```javascript
controls //网页显示默认控件
poster = "图片路径" //Video的独有控件，能改变视频在网页中显示的封面
muted //静音
autoplay //自动播放,需要配合静音使用,对音频无效
loop //循环播放
preload: none/metadata/auto; //是否预加载
    不进行预加载/部分预加载(一般都使用这个)/全部预加载
```



判断浏览器支持情况：

```javascript
.canplayType() //返回probably或maybe，返回空不支持;
```



媒体事件：

```javascript
.onplay: 媒体开始播放时触发;
.onpause: 媒体暂停时触发;
.onended: 媒体播放结束时触发;
.oncanplay: 浏览器能够开始播放媒体数据,但不确定以当前速率能否顺利播放完媒体;
//已经获得媒体数据，但还不知道每一帧的数据
.ondurationchange: 媒体的duration发生变化时触发;
//缺点如果资源在本地,加载速度很快的情况下,可能不会触发。线上使用没问题; 
```



属性：

```javascript
.currentSrc //返回资源链接(需要媒体数据加载完成后才能获取到)
.duration //媒体总时长(需要媒体数据加载完成后才能获取到)
.currentTime //返回或设置资源当前时间
.volume //音量[0-1],可读可写
.playbackRate //读取或设置媒体资源的播放速率（大于1快放，小于1慢放，无倒放）
.paused/.ended/.seeking //查询媒体播放状态，返回true/false
    是否暂停/是否结束/是否在请求修改某一播放位置
.played/.buffered/.seekable //返回一个TimeRanges对象
    标明已播放的时间范围/确定已缓存媒体文件/可以对当前媒体资源进行请求
    TimeRanges对象的length属性为部分时间段，end(i)返回已播放时间段的结束时间,start(i)返回已播放时间段的开始时间
```



方法：

```javascript
.play() //播放
.pause() //暂停
.load() //重置媒体元素并重新载入媒体，可以终止正在进行的任务或事件
//可以用在上一曲下一曲上
```

