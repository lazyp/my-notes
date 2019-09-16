在使用git的时候经常会commit一次又一次，但是又不希望正式版本库里面存在很多这种不完全的`commit`记录，这时候就想把`commit`记录删除，把两个或者n个提交记录合并成一个正式的完整版的`commit`。

##### 第一步： 运行git log命令，查看commit历史记录

>比如总共有三次提交，但是可能这三次提交要提交的代码都是一样，后面两个提交稍微修正一个问题或者是格式，所以我并不想在git提交历史中出现两个无效的，非终极的提交。

##### 第二步：选择你需要合并的最早提交记录**之前**的commit版本号

> 例如你要把first commit、second commit、third commit合并到一个提交里面，那你就找到first commit之前的那次提交的commit版本：af703fa022d6bb4333e3945087215e1c7a4c4e86

##### 第三步： 运行 git rebase -i commit_id(替换为上面找到的版本号)

>本例中，我们运行git rebase -i af703fa022d6bb4333e3945087215e1c7a4c4e86

##### 第四步: 在英文输入模式下进入编辑模式，将第二次和第三次提交前面的pick改为squash ,然后按esc键退出编辑模式，输入wq保存，这时候会跳出一个编辑窗口让你输入合并之后的commit信息，修改完成之后保存关闭,就将commit记录合并完成了。

>引用 https://www.iyuxy.com/git-he-bing-commitji-lu/