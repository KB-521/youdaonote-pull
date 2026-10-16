file表示file控件内的每一个被选择的文件对象；

fileList为这些file对象的列表；



fileReader对象：

```javascript
//负责把文件读入内存,并读取文件中的数据
var reader = new FileReader(); 
reader.readAsText(file); //讲文件中的数据读取为文本数据
reader.readAsBinaryString(file); //读取为二进制字符串
reader.readAsDataURL(file); //读取为DataURL字符串
reader.readAsArrayBuffer(file); //读取为一个ArrayBuffer对象
reader.abort(); //中断读取操作
```

fileReader读取事件：

```javascript
reader.onabort = fun; //数据读取中断时触发
reader.onprogress= fun; //数据读取中触发
reader.onerror= fun; //数据读取出错时触发
reader.onload= fun; //数据读取成功完成时触发
reader.onloadstart= fun; //数据开始读取时触发
reader.onloadend= fun; //数据读取完成时触发，无论成功与否;
```



Blob对象：

fileReader对象是继承Blob对象的；

Blob对象是可以裁剪的(数据分段上传原理)

```javascript
.slice(); //可以进行裁剪的方法
```



获取drop中的file对象：

```javascript
e.dataTransfer.files //能获取在e中的file对象
//获取drop中拖拽上传的file对象
```

