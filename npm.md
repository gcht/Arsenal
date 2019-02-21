
# npm cli
- 一个cli可以有多个bin命令，例如
```
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
/usr/local/bin/mdf -> /usr/local/lib/node_modules/ucf-mdf/bin/ucf-init.js
```
- 多个cli可能会造成bin命令的指向改变（后安装的覆盖前面的），后者安装的起作用
> 发现被覆盖了，就重新执行以下npm install -g xxxx

# npm 发布流程
1. 在终端输入 npm login
出现```Logged in as gcht163 on https://registry.npmjs.org/.```就可以
2. npm public

# npm 发布必填
package.json中的：    
- name
- version
- bin （cli填写）
