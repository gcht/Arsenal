# 切换NPM
- 切换NPM官方
```
   npm config set registry https://registry.npmjs.org
   npm config get registry
```   
 - 切换淘宝镜像：
 ```
    npm config set registry https://registry.npm.taobao.org
    npm config get registry
```
- 更改镜像地址的方法（以淘宝为例）：
```
  npm config set registry https://registry.npm.taobao.org --global
```
- 设置node源码的源：
```
  npm config set disturl https://npm.taobao.org/dist --global
```
  
# 发包
- 命令
```
  npm log
  npm publish
  npm version patch
  npm version prerelease --preid=alpha
```


# 更新发布的包
### 正式包
```
  npm version patch
  npm publish
```

### tag包  alpha
```
 npm version prerelease --preid=alpha
```
# 撤销指定版本包

```
    npm unpublish 包名@版本号
    npm unpublish mypackage_g@1.0.3
```

# 删除整个包
```
  npm unpublish xxx包名 --force
```
