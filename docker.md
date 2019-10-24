1.docker run -i -t aaa /bin/bash  打开伪终端交互的模式运行容器aaa   
> [利用docker打包软件，也会用到这个命令，更新详细的参数可以可参考] https://www.runoob.com/docker/docker-run-command.html

2.docker image ls 查看所有本地image镜像

3.docker ps -a 查看所有的容器container信息

4.docker container prune  移除所有的已终止的容器，kill后container引用还在

5.docker commit containerid imagename:version 保存在容器中的修改配置等信息；可以保存为新的镜像名或者直接更新当前镜
