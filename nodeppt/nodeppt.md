https://github.com/ksky521/nodePPT/blob/master/ppts/demo.md

创建
nodeppt create ppt-name
nodeppt create ppt-name.htm
nodeppt create ppt-name.html

启动
nodeppt start -p 8080 -d path/for/ppts -H 127.0.0.1

nodeppt start -c socket
扫描二维码手机上可以使用左右touch滑动

这种方式也可以
http://127.0.0.1:8080/md/demo.md?controller=socket

启用postMessage控制 没成功
http://127.0.0.1:8080/md/demo.md?_multiscreen=1

基本配置如下
title: 这是演讲的题目
speaker:  演讲者名字
url: 可以设置链接
transition: 转场效果，例如：zoomin
files: 引入js和css的地址，如果有的话~自动放在页面底部

目录关系：可以在md同级目录下创建img、js、css等文件夹，然后在markdown里面引用，nodeppt默认会先查找md文件同级目录下面的静态资源，没有再找默认的assets文件夹下静态内容

支持的转场动画包括：

kontext
vkontext
circle
earthquake
cards
glue
stick
move
newspaper
slide
slide2
slide3
horizontal3d
horizontal
vertical3d
zoomin
zoomout
pulse

目前支持的单条动画效果包括：

moveIn
fadeIn
bounceIn
rollIn
zoomIn

导出ppt
pdf版
npm install -g phantomjs
nodeppt pdf http://127.0.0.1:8080/md/demo.md a.pdf
phantomjs版本可能较老，推荐在chrome浏览器中使用ctrl+P选择另存为pdf

html版
nodeppt generate ./ppts/demo.md -a -o output/path
导出目录下所有ppt，并且生成ppt list首页：
nodeppt path -o output/path -a

