#####linux 常用基础命令

1. `cd`切换目录命令  
>  `cd dir_name` #切换到dir_name目录   
>  ```cd -``` 返回前一次的目录    
>  `cd ~`返回当前用户的home目录   
>  `cd ..`返回上一层目录   

2. 切换到当前用户home目录: cd ~
3. which -a cmd_name #会在PATH环境变量里面的目录寻找命令的绝对路径
4. du -sh $dir_name //显示目录的磁盘占用空间
5. rm $file_name #删除文件
6. rm -r $dir_name #可删除整个目录
7. mkdir $dir_name #创建一个目录
8. kill $pid #结束一个进程
9. kill -9 $pid #强制结束一个进程
10. clear #清空terminal屏幕
11. man cmd_name # 查看命令帮助说明,eg. man clear
12. ls #查看当前目录下的所有文件和文件夹列表
13. ls -lha #查看包含'.'开始的隐藏文件和文件夹,以及详细的权限和创建时间,大小等信息
14. cp src_file to_path # 将src_file复制到to_path
15. cp -r src_dir to_dir #加`-r`参数可以复制目录
