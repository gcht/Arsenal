# git stash
> git stash list
> git stash push
> git stash pop



# git pull --rebase
重新建立base（基准），git fetch + git merge    
把当前的修改合提到最前面


# git rebase
- 合并多次提交：    
> `git rebase -i HEAD~2`     
i的意思是：interactive，HEAD~2为在历史的前两个提交，同理，HEAD~4就是历史的前四个提交。

具体如下：    
1. 命令行输入：git rebase -i HEAD~2 （i的意思是：interactive，HEAD~2为在历史的前两个提交，同理，HEAD~4就是历史的前四个提交。）

2. vim出现如下所以文件信息，前面两行就是你的提交信息，比如第一行分别对应为：pick(使用提交)、56a06ef(提交的ID)、change 1: remove one blank line(提交的描述信息)    

3. 将第二行的pick改成s, 也就是squash(挤压合并)，作用是：使用提交，将此提交与之前的提交合并。   然后保存文件退出vim。    

4. 提交你的代码，git commit -a, vim出现如下所以文件信息：注意看：第4行和第8行分别对应这你第一次和第二次的提交描述信息，这时你就要将这两条描述信息合并为一条。

5. 将之前的两条提交描述信息，修改合并为一条，然后保存退出vim，如下所示：

6. 保存退出后，push代码：git push origin master -f (注意：因为时rebase操作，所以要加-f, 强制push), 推送完成， 如下所以，完成将两个提交合并为一个。

参见：【https://blog.csdn.net/jerechen/article/details/89556281】(https://blog.csdn.net/jerechen/article/details/89556281)





# git cherry-pick 32259aa35d0702d2d05c648938798f9a5bd4b9e7


# git checkout
> `git checkout .`  
> `git checkout index.js`  



# git branch -a
> `git branch -b`  
> `git checkout xxx-branch`      创建新分支xxx-branch  
> `git checkout -b yan`  创建新分支yan,并切换过去  
# git branch -D
`git branch -D develop_gct` 删除develop_gct分支    
`git push origin --delete develop_diwork_gct1122`  删除远程develop_diwork_gct1122分支    



--------------------------------------------------
# git reset 
撤销同时销毁记录  
> git reset fa04a2 默认是保留reset
> `git reset HEAD --hard`  

撤销remote的master分支的记录  
> `git reset fa042c --hard`  
> `git push orgin master:master --force`   不加--force的话，会提示提交的记录比较老，不能提交 
保护分支会有提示：        
remote: GitLab: You are not allowed to force push code to a protected branch on this project.    
取消保护再push    





# git revert  
撤销某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次最新的提交到history中（git log）    
> `git revert HEAD`          撤销前一次 commit    
> `git revert HEAD^`         撤销前前一次 commit    
> `git revert fa042c` （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）撤销指定的版本。    

git revert是提交一个新的版本，将需要revert的版本的内容再反向修改回去。    
history版本会递增，不影响之前提交的内容    


--------------------------------------------------------------
# git push 
一般形式为` git push <远程主机名> <本地分支名>:<远程分支名> `     
例如     
`git push origin master：refs/for/master`    
即是将本地的master分支推送到远程主机origin上的对应master分支， origin 是远程主机名        
第一个master是本地分支名(即本地源，src)，第二个master是远程分支名(即远程目标，dst)。        

### 全称用法
> `git push origin mybranch:mybranch`      origin代表远程   src:dst     将本地`src分支`提交到`dst分支`    

-------------------------------------------------------
### 省略用法：        
- `git push origin mybranch` （省略了<dst>，等价于`git push origin master:master`）     
  > 如果远程分支被省略，如上则表示将本地分支推送到与之存在追踪关系的远程分支（通常两者同名），如果该远程分支不存在，则会被新建
    
- `git push origin :mybranch` （省略了<src>, 在origin上查找mybranch，用一个空的去更新它，就相当于删除了)
  > 谨慎使用！谨慎使用！谨慎使用!    
  
- git push origin test:master     (提交本地test分支 作为 远程的master分支)
  > 谨慎使用！谨慎使用！谨慎使用!

-----------------------------------------------
# git merge
- `git merge xxx-branch`    把xxx-branch分支合并到当前分支    
例如： 当前是master分支，想把develop分支合并到master分支，就执行  `git merge develop`
> 合并解决冲突后，相当于修改，需要重新git add、 git commit、  git push




--------------------------------------

# git log

- `git log`    
- `git log -oneline`                   简洁查看，每次记录都只显示一行     
 > 相当于`git log --pretty=oneline  `  
- `git log -5`                         显示最近的5次log    
- `git log -p `  
