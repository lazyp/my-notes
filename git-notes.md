#### 基础命令 ####
>git clone remote_url_addr #克隆项目   
>git pull origin master  #拉取项目代码   
>git push origin master # 推送代码到远端仓库   
>git push --force origin master    #强制推送代码到远端仓库,当本地做了强制回滚,修改等操作,普通的push会被reject,必须加一个参数--force,慎用   
>git status #查看文件更改情况   
>git add file_name #将一个文件添加到暂存区   
>git add .   #可以将所有的更改过的文件添加到暂存区    
>git commit -m "修改说明" #提交

#### 回滚本地commit ####
> Delete the most recent commit, keeping the work you've done:    
> git reset --soft HEAD~1

> Delete the most recent commit, destroying the work you've done:    
> git reset --hard HEAD~1

> 撤销(回退)某次commit   
> git revert commit_hash_id **(revert会产生一个新的commit,回退代码)**

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
