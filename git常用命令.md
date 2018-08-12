
## git checkout
> `git checkout .`  
> `git checkout index.js`  



## git branch -a
> `git branch -b`  
> `git checkout xxx-branch`      创建新分支xxx-branch  
> `git checkout -b yan`  创建新分支yan,并切换过去  

## git reset 
撤销同时销毁记录  
> git reset fa04a2 默认是保留reset
> `git reset HEAD --hard`  

撤销remote的master分支的记录  
> `git reset fa042c --hard`  
> `git push orgin master:master --force`   不加--force的话，会提交提交的记录比较老，不能提交 

## git revert  
撤销某次操作，此次操作之前和之后的commit和history都会保留，并且把这次撤销作为一次最新的提交到history中（git log）    
> `git revert HEAD`          撤销前一次 commit    
> `git revert HEAD^`         撤销前前一次 commit    
> `git revert fa042c` （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）撤销指定的版本。    

git revert是提交一个新的版本，将需要revert的版本的内容再反向修改回去。    
history版本会递增，不影响之前提交的内容    


--------------------------------------

## 日志

> `git log`    
> `git log -oneline`                   简洁查看，每次记录都只显示一行     
> `git log --pretty=oneline  `  
> `git log -5`                         显示最近的5次log    
> `git log -p `  
