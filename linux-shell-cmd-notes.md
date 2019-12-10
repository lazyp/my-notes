#### linux 常用基础命令
1.安装软件命令
> redhat/centos: `yum install xxxx`   
> debain/ubuntu: `apt-get install xxx`  
  
2.`cd` 切换目录命令  
> `cd dir_name` #切换到dir_name目录   
> `cd -` 返回前一次的目录    
> `cd ~`返回当前用户的home目录   
> `cd ..`返回上一层目录   

3.`ls` #查看当前目录下的所有文件和文件夹列表  
> `ls -lha` #查看包含'.'开始的隐藏文件和文件夹,以及详细的权限和创建时间,大小等信息  
> `ls -ld` #加一个`-d`参数,可查看当前目录的信息  

4.`man cmd_name` 查看命令的使用说明帮助文档,非常实用    
>  eg. `man ls` 查看`ls`命令的使用说明  

5.`which -a cmd_name` #会在PATH环境变量里面的目录寻找命令的绝对路径  

6.`du -sh $dir_name` #显示当前目录的磁盘占用空间  
> `du -d1 -h $dir_name` #显示当前目录下第一层子目录的磁盘占用空间信息

7.`rm $file_name` #删除文件  
> `rm -r $dir_name` #可删除整个目录  
> `rm -f xxx` #强制删除,不会给出提示对话框  

8.`mkdir $dir_name` #创建一个目录  
> `mkdir {dir1,dir2,dir3}` #同时创建3个目录  

9.`kill $pid` #结束一个进程   
> `kill -9 $pid` #强制结束一个进程   

10.`clear` #清空terminal屏幕   

11.`netstat` #查看本机网络连接信息    
> `netstat --help` 查看命令说明   
> `netstat -ant` 查看所有的tcp连接信息  
> `netstat -tnl` 查看tcp listening的端口情况  
> `netstat -tnlp | grep 8080` 或 `lsof -i:8080` 查看占用端口8080的进程

12.`cp src_file to_path`# 将src_file复制到to_path   
> `cp -r src_dir to_dir` #加`-r`参数可以复制目录  

13.`mv source_dir dest_dir` #命令移动目录位置,也可以重命名目录名字   

14.`ctrl+r` #可以搜索历史命令   

15.`top` #命令可查看当前系统负载,cpu使用率,内存,以及进程信息.默认top命令是动态更新的    
> `top -p pid` #可查看指定pid的进程运行信息    
> `top -Hp pid` #可列举指定pid进程里面的所有线程运行信息   

16.`ps` #命令也是查看系统进程信息的,查看的是一份静态的快照
> `ps aux` #查看系统所有的进程信息
> `ps pid` #查看指定进程信息的一份快照

17.`tar` #打包,解压命令
> `tar -xvf xxx.tar.gz` #解压一个压缩包
> `tar -cvzf xxx.tar.gz xxx` #压缩一个文件夹(xxx)

18. `lsof -i` #查看网络连接的一些信息

19. `nohup` #后台运行程序
> `nohup abc.sh &` 日志默认输出到nohup.out文件
> `nohup abc.sh > abc.log 2>&1 &` 日志重定向到abc.log文件，错误异常日志也重定向输出到abc.log

20. `history` #使用命令历史记录   
> `export HISTTIMEFORMAT="%F %T "` #可以现实使用命令的时间



