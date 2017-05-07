npm run新建的这个 Shell，会将当前目录的node_modules/.bin子目录加入PATH变量，执行结束后，再将PATH变量恢复原样。

npm run 本身有一个参数-s，表示关闭 npm 工具本身的输出， 只输出脚本产生的结果

| ：连接两个任务
"build-js": "browserify browser/main.js | uglifyjs -mc > static/bundle.js"

&& ：任务内部引用其他任务，子任务 先后 执行
"build": "npm run build-js && npm run build-css"

& ：任务内部引用其他任务，子任务 平行 执行
"commit": "npm run test & npm run commit"

并行
npm-run-all--parallel watch:html watch:js
串并行
npm-run-all clean lint--parallel watch:html watch:js

"lint": "jshint **/*.js"

*表示任意文件名，**表示任意一层子目录

"lint": "jshint **.js"
传参：
npm run lint --  --reporter checkstyle > checkstyle.xml

npm 脚本有pre和post两个钩子:
* prepublish，postpublish
* preinstall，postinstall
* preuninstall，postuninstall
* preversion，postversion
* pretest，posttest
* prestop，poststop
* prestart，poststart
* prerestart，postrestart
* prebuild，postbuild


{
  "name": "foo",
  "version": "1.2.5",
  "scripts": {
    "view": "node view.js"
  }
}

js:
console.log(process.env.npm_package_name); ==> foo

shell:
$npm_package_version


npm config set foo:port 80

npm 脚本还可以通过npm_config_前缀，拿到 npm 的配置变量，即npm config get xxx命令返回的值。比如，当前模块的发行标签，可以通过npm_config_tag取到
