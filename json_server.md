https://github.com/typicode/json-server

npm install -g json-server

db.json
```json
{
  "posts": [
    {
      "id": 1,
      "title": "json-server",
      "author": "typicode"
    },
    {
      "id": 2,
      "title": "我是posts2",
      "author": "typicode"
    },
    {
      "id": 3,
      "title": "我是posts3",
      "author": "typicode"
    },
    {
      "id": 4,
      "title": "我是posts4",
      "author": "typicode"
    },
    {
      "id": 2,
      "title": "我是posts2",
      "author": "typicode"
    },
    {
      "id": 5,
      "title": "我是posts5",
      "author": "typicode"
    },
    {
      "id": 6,
      "title": "我是posts6",
      "author": "typicode"
    },
    {
      "id": 7,
      "title": "我是posts7",
      "author": "typicode"
    },
    {
      "id": 8,
      "title": "我是posts8",
      "author": "typicode"
    },
    {
      "id": 9,
      "title": "我是posts9",
      "author": "typicode"
    },
    {
      "id": 10,
      "title": "我是posts10",
      "author": "typicode"
    }
  ],
  "comments": [
    {
      "id": 1,
      "body": "some comment",
      "postId": 1
    }
  ],
  "profile": {
    "name": "typicode"
  }
}
```
```
json-server --watch --port 8888 db.json

http://10.1.50.186:8888/posts
http://10.1.50.186:8888/posts/1
http://10.1.50.186:8888/posts?id=1&author=typicode
http://10.1.50.186:8888/posts?_start=0&_end=5
http://10.1.50.186:8888/posts?_start=0&_limit=5
/posts?_sort=views&_order=DESC
/posts/1/comments?_sort=votes&_order=DESC/ASC
```

jqury往服务器添加数据,其他方法类推
```jqury
$.ajax({
    type: 'post',
    url: 'http://localhost:3003/news',
    data: {
      "id": 3,
      "title": "我是新加入的新闻",
      "date": "2016-08-12",
      "likes": 0,
      "views": 0
    }
  }
)
```

动态生成数据：
db.js
```js
module.exports = function() {
  var data = { users: [] }
  // Create 1000 users
  for (var i = 0; i < 1000; i++) {
    data.users.push({ id: i, name: 'user' + i })
  }
  return data
}
```
json-server db.js
```
数据生成器:
faker:不但拥有几乎全部常用的数据格式，而且还有中英德法等多种语言的数据。但是在实际测试中发现，faker 对中文数据的支持还是以西方文字为基础，并不能很好的模拟中文
chance
mockjs:
npm install mockjs --save
不能跨域使用
与某些框架中的路由处理逻辑冲突
无法定义复杂的数据结构
无法自定义较为复杂的路由
```

```js
let Mock  = require('mockjs');
let Random = Mock.Random;

module.exports = function() {
  var data = { 
      news: []
  };
  
  var images = [1,2,3].map(x=>Random.image('200x100', Random.color(), Random.word(2,6)));

  for (var i = 0; i < 100; i++) {
      
    var content = Random.cparagraph(0,10);

    data.news.push({
         id: i, 
         title: Random.cword(8,20),
         desc: content.substr(0,40),
         tag: Random.cword(2,6),
         views: Random.integer(100,5000),
         images: images.slice(0,Random.integer(1,3))
    })
  }

  return data
}
```

json-server.json:
```json
{
    "host": "0.0.0.0",
    "port": "3003",
    "watch": false,
    "delay": 500,
    "quiet": true,
    "routes": "./routes.json"
}
```

routes.json
```json
{
  "/news/:id/show": "/news/:id",
  "/topics/:id/show": "/news/:id",
    
}
```
访问 /news/1/show 和 topics/1/show 均返回指定的 /news/1 内容。

```
// 获取图片数量为3，且标签字数为2的新闻
GET /news?images.length=3&tag.length=2

// 选取浏览量在2000-2500之间的新闻
GET /news?views_gte=2000&views_lte=2500

// 选择tag属性不是 "国际新闻" 的分类
GET /news?tag_ne=国际新闻

// 查找title中含有 "前端" 字样的新闻 
GET /news?title_like=前端

// 查找新闻全部字段包含 "强拆" 字样的数据
GET /news?q=强拆

// 获取包含下级资源的数据, 使用 _embed
GET /news?_embed=comments
GET /news/1?_embed=comments

// 获取包含上级资源的数据, 使用 _expand
GET /news?_expand=post
GET /news/1?_expand=post
```

json server 同样可以作为诸如 Express 之类框架的中间件使用


