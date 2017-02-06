npm config get cache
npm cache ls react
npm cache clean

npm install react@3.9.1
    --force
    -S, --save 安装包信息将加入到dependencies（生产阶段的依赖）
    -D, --save-dev 安装包信息将加入到devDependencies（开发阶段的依赖），所以开发阶段一般使用它
    -O, --save-optional 安装包信息将加入到optionalDependencies（可选阶段的依赖）
    -E, --save-exact 精确安装指定模块版本
    
npm uninstall react

npm update react

npm outdated

npm ls -g 

npm view react
npm view gulp dependencies/repository.url/contributors
npm info react
npm show react
npm v react

npm config set <key> <value> [-g|--global]
npm config get <key>
npm config delete <key>
npm config list
npm config edit
npm get <key>
npm set <key> <value> [-g|--global]

npm start [-- <args>]
npm stop [-- <args>]
npm restart [-- <args>]
npm test [-- <args>]

