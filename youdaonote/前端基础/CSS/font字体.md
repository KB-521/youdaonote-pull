字体大小：

```javascript
16px  //默认字体大小
10em  //是当前元素的父元素的字体大小*10
10rem  //是根元素(html)的字体大小*10
1vw/1vh  //将屏幕视口的宽和高分成100份，其中一份的宽/高
```

字体粗细：

```javascript
font-weight:100-900/normal(默认值:400)/lighter(更细)/bold(更粗)；
```

斜体:

```javascript
font-style:italic;
```



```javascript
font:style weight size/line-height font-family;
```



自定义字体库(字体先放服务器上)：

```javascript
@font-face{
    font-family:'自定义名称';
    scr:url('······.ttf');/*兼容IE*/
    scr:
        /*多格式兼容全部浏览器*/
        url('······.eot?iefix')format('embedded-opentype'),
        url('······.woff')format('woff'),
        url('······.ttf')format('truetype'),
        url('······.svg')format('svg');
}```



 谷歌字体库：https://fonts.google.com

 