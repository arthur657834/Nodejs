npm config set registry=http://registry.npmjs.org

npm init
npm adduser

npm whoami
npm login

npm publish


npm owner ls <package name>
npm owner add <user> <package name>
npm owner rm <user> <package name>

npm version 0.1.1
npm publish


npm社区版本号规则采用的是semver（语义化版本），主要规则版本格式：主版本号.次版本号.修订号，版本号递增规则如下：

主版本号：当你做了不兼容的 API 修改，
次版本号：当你做了向下兼容的功能性新增，
修订号：当你做了向下兼容的问题修正。

package.json
"private":true 
告知npm不能发布该模块  

vi hello.js 
exports.Hello = function ( name ) { 
        console.log( "Hello " + name ); 
} 

vi package.json 
{
  "name": "node_module_demo",
  "version": "1.0.0",
  "description": "",
  "main": "hello.js",
  "private": false,
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/arthur657834/node_module_demo.git"
  },
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/arthur657834/node_module_demo/issues"
  },
  "homepage": "https://github.com/arthur657834/node_module_demo#readme"
}