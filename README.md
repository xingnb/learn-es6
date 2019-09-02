# es6个人学习demo

## demo01

### 安装babel 
npm install -g babel-cli
npm install --save-dev babel-preset-es2015 babel-cli
添加**.babelrc**
*
{
    "presets":[
        "es2015"
    ],
    "plugins":[]
}
*
### 简化命令
"scripts": {
    "build": "babel src/index.js -o dist/index.js"
}