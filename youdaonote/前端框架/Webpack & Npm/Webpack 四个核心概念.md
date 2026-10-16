1. Entry：告诉webpack入口文件位置；

1. Output：告诉webpack把编译好的文件放在哪；

1. Loaders：告诉webpack在添加到依赖图之前如何装换一个文件；

1. Plugins：在编译过程中添加你想要的任何操作；



import("url")；动态引入文件，用到再加载；

需要加载@babel/plugin-syntax-dynamic-import插件才能使用；