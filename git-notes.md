#### 基础命令 ####
>git clone remote_url_addr #克隆项目
>git pull origin master  #拉取项目代码
>git push origin master # 推送代码到远端仓库
>git push --force origin master #强制推送代码到远端仓库,当本地做了强制回滚,修改等操作,普通的push会被reject,必须加一个参数--force,慎用 

#### 回滚本地commit ####
> Delete the most recent commit, keeping the work you've done:
> git reset --soft HEAD~1

> Delete the most recent commit, destroying the work you've done:
> git reset --hard HEAD~1

#### git  项目迁移方案 ####
> git clone --mirror 地址
> git push --mirror 新的地址

#### 修改上一次提交的用户名和email可以用以下命令 ####
> git commit --amend --author="Author Name <email@address.com>"

#### 修改上一次commit的描述可以用如下命令####
>git commit --amend
