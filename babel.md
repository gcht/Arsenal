参考链接：
[https://www.cnblogs.com/lsgxeva/p/7758184.html](https://www.cnblogs.com/lsgxeva/p/7758184.html)

# babel转移插件和转移器

# bael命令
- 方法1    
```
npm run build

```
- 方法2    
是你需要可以进入node_modules文件夹，再进入.bin文件夹，然后执行在命令行中执行babel src -d lib。

### 经典命令
babel src -d lib
> 这个命令目的是把src文件夹下的文件都转译，转译后的文件放到lib目录下。

# 配置与命令
- 在.babelrc中配置的选项都可以通过命令行添加，    
```比如在命令行执行 babel src -d lib --presets=env ```    
等价于    
```在.babelrc中配置 "presets":["env"]```    
当然.babelrc要明显方便很多。

关于.babelrc的注意点如下。    
- 1、如果没有.babelrc文件，或者没有在其他文件中设置过babel的presets的配置选型，并且命令行中也没有配置--presets，那么代码是不会转译的。原es6代码什么样，转译后的代码还是什么样。

- 2、如果你的.babelrc或者你的命令行使用了你没有安装的转译器（presets），代码就会报错

- 3、但.babelrc中的配置跟你在命令行中使用的配置```冲突```的时候，以```.babelrc```中的配置```为准```
```
  {
    "presets":["env"]
  }
```

### .babelrc的替代方案
如果你不想生成.babelrc文件，你可以在你的package.json文件中对babel进行配置。    
如果你使用gulp或者webpack之类的管理工具的话，也可以在这里工具的配置选项里添加babel的配置选项。    
以下以在package.json中配置为例。    
注意：```在package.json中配置babel等同于使用.babelrc文件   ```     
```
  {
  "name": "es6",
  "version": "1.0.0",
  "description": "",
  "main": "arrow.js",
  "scripts": {
    "build": "babel src -d lib --comments=true"
  },
  "babel":{
    //babel选项
    "presets":["es2015"],
    "comments":false
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "babel-cli": "^6.24.1",
    "babel-loader": "^7.1.1",
    "babel-preset-env": "^1.6.0",
    "babel-preset-es2015": "^6.24.1",
    "babel-preset-react": "^6.24.1",
    "webpack": "^3.2.0"
  }
}
```

# 常见babel转译器和插件
### babel-preset-env
最常见，可以让代码兼容不同版本的浏览器和node。 如果不配置env选项，该转译器等同于babel-preset-latest
```
{
  "presets": [
    ["env", {
      "targets": {
        "browsers": ["last 2 versions", "safari >= 7"]
      }
    }]
  ]
}
```
### babel-preset-es2015
### babel-preset-latest 废弃!使用babel-preset-env
### babel-preset-react
转译器，剥离流类型并将JSX转换为createElement调用，主要在转译react代码的时候使用。
### 兼容ie的转译器
要兼容老版本的ie浏览器，可以使用对应的es3和es5插件
- es3-member-expression-literals
- es3-property-literals
- es5-property-mutators

# babel常见配置项
babel配置项在命令行里的使用规则：  bebel xx  --name=value  
例如：
```
  babel src -d lib --preset=es2015
```
## babelrc
## env
## ignore
忽略foo.js
```
{
    "presets":["env"],
    "ignore":["foo.js"]
}
```
和ignore对应的还有only选项，表示只转译某些文件

### mimified
是否压缩转译后的代码，默认是false，不压缩
```
{
    "presets":["env"],
    "ignore":["foo.js"],
    "minified":true
}
```

### plugins和presets的顺序
- 如果同时存在plugins和presets，则先使用plugins转译
- plugin的调用顺序是从第一个到最后一个，
- presets的调用的顺序是相反的，从最后一个到第一个


## babel-register
会改写require命令，为他加上一个钩子，每当加载js\jsx、es、es6等后缀文件时，都会先用babel进行转码    
不需要手动对index.js转码了
(1) 安装
```
$ npm install --save-dev babel-register
```

(2) 使用
必须先加载babel-register,再require其他js文件

```
require("babel-register");
require("./index.js");
```





# babel在webpack中使用

确保至少2个插件安装
- babel-preset-env
- babel-loader
例如：    
```
{
  "name": "es6",
  "version": "1.0.0",
  "description": "",
  "main": "arrow.js",
  "scripts": {
    "build": "babel src -d lib"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "babel-cli": "^6.24.1",
    "babel-loader": "^7.1.1",
    "babel-preset-env": "^1.6.0",
    "babel-preset-react": "^6.24.1",
    "webpack": "^3.2.0"
  }
}
```
## 在webpack.config.js中配置
```
var path = require("path");
module.exports = { 
    entry: './src/person.js', 
    output: { 
        path: path.resolve(__dirname,"lib"), 
        filename: 'person.compiled.js', 
    }, 
    module: { 
        loaders: [{ 
            test: /\.js$/, 
            exclude: /node_modules/, 
            loader: 'babel-loader',
            query:{
                presets:["env"]
            } 
        }] 
    } 
} 
```
query选项为.babelrc中的配置选项。    
在webpack中设置了query字段后，就不再需要.babelrc文件了。







































