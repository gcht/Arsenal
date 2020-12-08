
# npm cli
- 一个cli可以有多个bin命令，例如
```
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
```
- 多个cli可能会造成bin命令的指向改变（后安装的覆盖前面的），后者安装的起作用
> 发现被覆盖了，就重新执行以下npm install -g xxxx


# npm 切换淘宝镜像
### 查看
```
  npm config get registry
```

### 更改镜像地址的方法（以淘宝为例）：
```
  npm config set registry https://registry.npm.taobao.org
  npm config get registry
  npm config set registry https://registry.npm.taobao.org --global
  npm config get registry
```
### 设置node源码的源：
```
  npm config set disturl https://npm.taobao.org/dist --global
```
### 配置后可通过下面方式来验证是否成功      
```
  npm config get registry```    
```
### 查看指定包的信息    
```
  npm info xxxx(包名)
```

### 临时使用
```
  npm --registry https://registry.npm.taobao.org install xxx
```
# 切换NPM官方
```
  npm config set registry https://registry.npmjs.org
  npm config get registry
```





# 3 发包
### npm 发布流程
- 1. 在终端输入 npm login
出现```Logged in as gcht163 on https://registry.npmjs.org/.```就可以
- 2. npm public

> npm 发布必填
> package.json中的：    
> - name
> - version
> - bin （cli填写）


### 发布
```
  npm log
  npm publish
  npm info xxxx(包名)
```


### 更新一个已经发布的包

```
  npm version patch
  npm publish
  npm info xxxx(包名)
  
  npm view abcdemo version       //查看现在包的版本

  其他命令：
  npm version patch  //修改x.y.z中z的数字升级，补丁版本
  npm version minor  //修改x.y.z中y的数字提升，小修改版本
  npm version major  //修改x.y.z中x的数字提升,大版本
```

# 撤销指定版本包

```
    npm unpublish 包名@版本号
    npm unpublish mypackage_g@1.0.3
```

### 删除整个包
```
  npm unpublish xxx包名 --force
```



### 6.管理包权限

查看模块拥有者
```
$ npm owner ls

$ npm owner ls hello_freedom
```
添加一个发布者
```
$ npm owner add

$ npm owner add freedom hello_freedom
```
删除一个发布者
```
$ npm owner rm

$ npm owner rmfreedom hello_freedom
```


### 8.分析包

查看当前项目引入了哪些包
```
npm ls
```


# npm 升级node
mac 系统需要切换到root用户 sudo -u
- 查看版本
npm -v
node -v
- 更新npm版本
  npm install -g npm
- 更新node版本
先清除npm缓存：npm cache clean -force    
然后安装n模块：npm install -g n    
升级node.js到最新稳定版：n stable      

先清除npm缓存：npm cache clean -force  
先清除npm缓存：npm cache clean -force 


# npm 清除npm缓存
 [Node.js中相同模块是否会被加载多次？](https://blog.csdn.net/weixin_41049850/article/details/79510059)
1. Node.js会从当前模块所在目录的node_modules（这里怎么不遵守Unix习惯，而使用了下划线呢？）开始找起，如果没找到再会去找上级目录的node_modules，直到根目录为止
2. 手动安装npm install xxx 的xxx模块会和其他模块的***间接依赖***重复
- 好处 多版本共存
  当然，Node.js这种“重复加载”的影响也并非完全是负面的，至少它天然的解决了多版本共存的问题。  
  例如，
  express v2.5.2依赖mime v1.2.4，    
  但我们程序自身又想使用mime v1.2.5。    
  此时，express内部自然使用mime v1.2.4，而我们自己的程序使用的便是mime v1.2.5。    
- 缺点 重复安装
  - 想避免这种重复加载，这就必须手动地删除模块内部被间接依赖的模块，将其移动到模块查询路径的```公用部分``上了。
  - 就目前看来，这些操作必须```手动```进行，因为npm在安装模块时不会关心依赖的模块是否已经安装过了（例如在NODE_PATH环境变量标识的路径里），它一定会重新下载所有依赖的模块。
  - 如果您使用的是托管形式的Node.js服务，则很有可能无法做到这一点。

   
