title: devops-boltman
speaker: xulj
url: https://github.com/ksky521/nodePPT
transition: cards
files: /js/demo.js,/css/demo.css

[slide]

# devops-boltman
## 演讲者：xulj

[slide]

# 封面样式2 {:&.flexbox.vleft}
## 左对齐

[slide style="background-image:url('/img/bg1.png')"]

## 使用背景

[slide]
## 使用.class/#id/自定义属性样式
----

```javascript
alert('nodeppt');
```
[slide]
## 单条动画
----

* 上下左右方向键翻页
    * 列表支持渐显动画 {:&.moveIn}
    * 支持多级列表
    * 这个动画是moveIn
	
[slide data-transition="vertical3d"]
## 单页的转场动画 这是一个vertical3d的动画

[slide]
## 插入html代码
<div class="file-setting">
    <p>这是html</p>
</div>
<p id="css-demo">这是css样式</p>
<p>具体看下项目中 ppts/demo.md 代码</p>
<script>
    function testScriptTag(){

    }
    console.log(typeof testScriptTag);
</script>
<style>
#css-demo{
    color: red;
}
</style>

[slide data-outcallback="outcallback" data-incallback="incallback"]
## 当进入此页，就执行incallback函数
## 当离开此页面，就执行outcallback函数

[slide]

### 市面上主要的css预处理器：less\sass\stylus
---
 |less| sass | stylus
:-------|:------:|-------:|--------
环境 |js/nodejs | Ruby | nodejs
扩展名 | .less | .sass/.scss | .styl
特点 | 老牌，用户多，支持js解析 | 功能全，有成型框架，发展快 | 语法多样，小众
案例/框架 | [Bootstrap](http://getbootstrap.com/) | [compass](http://compass-style.org) [bourbon](http://bourbon.io) |

[slide]
### 插入iframe
<iframe data-src="http://www.baidu.com" src="about:blank;"></iframe>

[slide]
Slide.on('update', function(i, itemIndex, cls) {
//接受三个参数：
//* 当前slide的index
//* itemIndex当前slide进入的第几个build动画，从1开始
//* 方向pageup/pagedown
    Puff.add('#FFC524' /*colors[i % 6]*/ , ctx, 20, 700, width / 2, height / 2, width / 1.8, 400);
    clearInterval(timer);
    //第十三个有动效
    if (i === 3 || i === 4) {
        timer = setInterval(function() {
            Puff.draw(1);
        }, 1E3 / FPS);
    }

})

[slide]

## 主页面样式
### ----是上下分界线
----

nodeppt是基于nodejs写的支持 **Markdown!** 语法的网页PPT，当前版本：1.4.2

Github：https://github.com/ksky521/nodePPT
