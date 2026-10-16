Geolocation API：

```javascript
window.navigator.geolocation //对象返回经纬坐标等元数据信息
```



获取当前地理位置：

```javascript
navigator.geolocation.getCurrentPosition(suc,err,obj);
//suc:成功回调，有参数option对象
//err:失败回调，有参数error对象
//obj:可选参数
```

option对象属性：

```javascript
accuracy: 经纬度的精度;
altitude: 海拔; //电脑一般获取不到，返回0/null(跟浏览器有关)
altitudeAccuracy: 海拔精准度; //电脑一般获取不到，返回0/null
heading: 设备前进的方向; //电脑一般获取不到，返回0/null
latitude: 纬度
longitude: 精度
speed: 设备前进的速度 //电脑一般获取不到，返回0/null
timestamp: 获取地理位置信息的时间; //1970/01/01至今的毫秒数
```

error对象属性：

```javascript
code属性参数: 1/2/3;
//用户拒绝了位置服务/获取不到位置信息/获取信息超时
message属性: 错误信息描述字符串;
```

obj对象：

```javascript
enableHighAccuracy: true/false; //是否要求高精准度位置信息
timeout:1000; //超时限制
maximumAge:1000; //缓存有效时间，若为0则无条件重置获取位置信息
```



监视位置信息：

```javascript
id = navigator.geolocation.watchPosition(suc,err，obj);
//持续定期的自动获取用户当前地理位置信息，并同计时器一样有个位置标时
navigator.geolocation.clearwatch(id);
//停止获取位置信息
```

