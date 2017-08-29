#### 基础命令 ####
>git clone remote_url_addr #克隆项目   
>git pull origin master  #拉取项目代码   
>git push origin master # 推送代码到远端仓库   
>git push --force origin master    #强制推送代码到远端仓库,当本地做了强制回滚,修改等操作,普通的push会被reject,必须加一个参数--force,慎用   
>git status #查看文件更改情况   
>git add file_name #将一个文件添加到暂存区   
>git add .   #可以将所有的更改过的文件添加到暂存区    
>git commit -m "修改说明" #提交   
>git merge --no-ff dev_branch #合并分支dev_branch 到当前分支,加了--no-ff参数,避免丢失分支信息   

>git checkout 命令总结
> >`git checkout branch` #分支切换      
> >`git checkout -b branch` #创建分支,并且切换到新分支     
> >`git checkout xxx_file` #恢复xxx_file,用index中的文件覆盖,注意针对这个文件的修改会全部丢失   
> >`git checkout .` #恢复整个工作空间,丢掉所有的未add的修改   
> >`git checkout another_branch -- xxx` # 从其他分支拉取`文件xxx`或者`文件夹`到当前分支空间   
> >`git checkout commit_hash_id` #切换到某一个历史状态,此时分支挂靠在一个commit上面,此时可以执行`git checkout -b newbranch`命令从当前状态创建出一个新分支    
> >`git checkout -p another_branch` #和其他分支做diff,并提示是否merge的交互式对话框    
> >`git checkout -p another_branch -- file` #和其他分支的某一个文件做diff,并提示是否merge的交互式对话框    

>git branch #分支操作命令      
> > `git branch or git branch --list` #查看的本地分支信息     
> > `git branch name` #创建一个分支,但不切换到新分支     
> > `git branch -d branch_name` #删除一个分支,此命令是删除本地分支信息,如果改分支存在于远程仓库,需要执行`git push origin :branch_name` 同步删除远程仓库中对应的分支信息    
> > `git branch -a` #列举所有的本地分支和远程分支列表      

>git stash #命令,暂时保存一个中间状态,比如修改了一些文件,但是此时不愿意add/commit,就可以用stash保存该状态到一个堆栈中.           
 >  > `git stash` #推进暂存堆栈     
 >  > `git stash pop` #弹出堆栈第一个   
 >  > `git stash list` #查看当前暂存堆栈中的元素,最前面一列时一个id标识`stash@{0}`    
 >  > `git stash id标识` #id标识就是上面命令显示的第一列,`eg. git stash stash@{0}`

 > `git push origin :branch_name` 删除远程分支,此条命令不会删除本地分支,只会删除远程对应的分支  
 
> `git tag` 标签功能   
>  >`git tag` 默认列举已有｀标签｀列表   
> >`git tag v1.6` 创建一个轻量级标签，名字为v1.6   
> >`git tag v1.6 -m "relase version 1.6"`  -m 选项则指定了对应的标签说明   
> >`git push origin tag_name` 推送一个标签到远程仓库 ，`eg. git push origin v1.6`    

#### 回滚本地commit ####
> Delete the most recent commit, keeping the work you've done:    
> git reset --soft HEAD~1

> Delete the most recent commit, destroying the work you've done:    
> git reset --hard HEAD~1

> 回滚到某个commitid    
> git reset --hard commitid(commit hash)    

> 撤销(回退)某次commit    
> git revert commit_hash_id **(revert会产生一个新的commit,回退代码)**     

>撤销`git add`操作      
>`git rm --cache xxxx` 从暂存区删除,这个不会删除物理文件  

#### 补丁制作和使用   
###### 第一种简单方案  
> 用`git diff`的结果就是一个patch,合并这类patch,直接需要用命令 `git apply patch.file`
>> 这种方案会丢失提交commit author信息等

###### 第二种方案 
> 用 `git format-patch -M other_branch` 命令生成patch文件,合并需要用`git am xxx.patch`文件   
>> -M选项表示这个patch要和那个分支比对   
>>  这种方案是根据两个分支的commit信息做对比生成补丁稳定,可能生成多个补丁文件.   

###### 两种方案对比 (http://www.cnblogs.com/y041039/articles/2411600.html)
> * 兼容性：很明显，git diff生成的Patch兼容性强。如果你在修改的代码的官方版本库不是Git管理的版本库，那么你必须使用git diff生成的patch才能让你的代码被项目的维护人接受。  
> * 除错功能：对于git diff生成的patch，你可以用git apply --check 查看补丁是否能够干净顺利地应用到当前分支中；如果git format-patch 生成的补丁不能打到当前分支，git am会给出提示，并协助你完成打补丁工作，你也可以使用git am -3进行三方合并，详细的做法可以参考git手册或者《Progit》。从这一点上看，两者除错功能都很强。  

> * 版本库信息：由于git format-patch生成的补丁中含有这个补丁开发者的名字，因此在应用补丁时，这个名字会被记录进版本库，显然，这样做是恰当的。因此，目前使用Git的开源社区往往建议大家使用format-patch生成补丁。



#### git  项目迁移方案 ####
> git clone --mirror 地址   
> git push --mirror 新的地址   

#### 修改上一次提交的用户名和email可以用以下命令 ####
> git commit --amend --author="Author Name <email@address.com>"

#### 修改上一次commit的描述可以用如下命令####
>git commit --amend

#### git submodule使用笔记 
> 1. 添加子模块,在项目的最上层目录执行```git submodule add 仓库地址 local路径```   
> 2. 命令执行完成，会在当前工程根路径下生成一个名为**“.gitmodules”**的文件，其中记录了子模块的信息。添加完成以后，再将子模块所在的文件夹添加到工程中即可。
> 3. 克隆一个带有子模块的项目可执行   
```git clone --recursive 仓库地址```    
  会自动将子模块的代码一起```clone```.(当然还有其他的方式,这种是最方便的方式咯)
> > 注意子模块是不会```detached```到任何```branch```,而是<code>detached</code>到一个<code>commit</code>的.
 
> 4. 子模块的项目有更新,此时更新子模块到最新,可使用命令 ```git submodule update --remote```,会更新依赖到最新的```commit```,最后执行如下命令,将最新的依赖信息```push```到远程仓库
```
  git add .
  git commit -m "update submodule"
  git push origin master
```
> 更加详细的介绍:https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97

#### git http/https proxy
> git config --global http.proxy "proxyurl"    
> git config --global https.proxy "proxyurl"    

