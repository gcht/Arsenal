
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
```npm config set registry https://registry.npm.taobao.org```     

配置后可通过下面方式来验证是否成功      
```npm config get registry```    
或     
```npm info express```

### 临时使用
npm --registry https://registry.npm.taobao.org install xxx





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
```


### 更新一个已经发布的包

```
  npm version patch
  npm publish
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
