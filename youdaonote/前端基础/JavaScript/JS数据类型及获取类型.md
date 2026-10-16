六种基本类型：number、string、boolen、null、undefined、object；

null和undefined值相等,数据类型不同;



Typeof：判断基本数据类型（null和function判断不了）；

Object.prototype.toString.call(i) 推荐代码使用，可以打印出系统所有数据类型（唯一缺陷：没办法判断自定义对象的类型）；

instanceof: 仅能判断对象的具体类型(只能判断对象)；

constructor：能判断他是否为构造函数；



未定义未声明typeof检测出来不一样的；