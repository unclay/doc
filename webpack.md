# webpack

## loaders

### Javascript loader

```bash
# babel,babel-loader依赖
$ npm install --save-dev babel-core babel-loader

# ES2015转码规则
$ npm install --save-dev babel-preset-es2015

# react转码规则
$ npm install --save-dev babel-preset-react

# ES7不同阶段语法提案的转码规则（共有4个阶段），选装一个
$ npm install --save-dev babel-preset-stage-0
$ npm install --save-dev babel-preset-stage-1
$ npm install --save-dev babel-preset-stage-2
$ npm install --save-dev babel-preset-stage-3
```
配置babel的规则

```json
{
  "presets": [
    "es2015",
    "stage-0"
  ],
  "plugins": []
}
```
配置webpack的loader
```json
{
  "test": /\.js$/,
  "loader": "babel",
  "exclude": /node_modules/
}
```

babel参考： [babel](http://www.ruanyifeng.com/blog/2016/01/babel.html)  
webpack.loader参考：[webpack.loader](http://webpack.github.io/docs/configuration.html#module-loaders)

### Css loader

```bash
# 把css转成DOM（style）插入到页面中
$ npm install --save-dev style-loader

# 加载css文件，例如 @import，url()等等加载进来的文件
$ npm install --save-dev css-loader

# 将css放进style标签，并插入到页面中
$ npm install --save-dev style-loader

# 后处理器，例如后处理浏览器兼容前缀等
$ npm install --save-dev postcss-loader

# 预处理器，less处理器(个人喜欢less)
$ npm install --save-dev less-loader

# 预处理器，sass处理器
$ npm install --save-dev sass-loader
```

配置webpack的loader，loader是从右到左执行的

```json
{
  "test": /\.less/,
  "loader": "style!css!postcss!less"
}
```

### Image loader

```bash
# 抓取打包css的图片，支持定义文件名的功能等
$ npm install --save-dev file-loader

# 封装file-loader, 新增支持小图转base64等功能
$ npm install --save-dev url-loader
```

配置webpack的loader

```json
{
  "test": /\.(png|jpg|gif)$/,
  "loader": "url?limit=8192&name=./img/[hash].[ext]"
}
```

url-laoder参考：[url-loader](https://segmentfault.com/a/1190000002551952)


### Vue loader

```bash
# 支持加载vue文件
$ npm install --save-dev vue-loader
```

配置webpack的loader

```json
{
  "test": /\.vue$/,
  "loader": "vue"
}
```
