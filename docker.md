1.docker run -i -t aaa /bin/bash  打开伪终端交互的模式运行容器aaa   
> [利用docker打包软件，也会用到这个命令，更新详细的参数可以可参考] https://www.runoob.com/docker/docker-run-command.html

2.docker image ls 查看所有本地image镜像

3.docker ps -a 查看所有的容器container信息

4.docker container prune  移除所有的已终止的容器，kill后container引用还在

5.docker commit containerid imagename:version 保存在容器中的修改配置等信息；可以保存为新的镜像名或者直接更新当前镜
> `docker commit -m="test update" -a="wangsir" 44652ba46352 wangsir/centos-test:7.4.1708`   
>-m:提交的描述信息  
>-a:指定镜像作者   
>44652ba46352：容器ID   
>wangsir/centos-test:7.4.1708:指定要创建的目标镜像名  

6. 具体例子，利用docker打包go项目:`docker run -v /local/goproject:/docker/goproject -w /docker/goproject -e GOPROXY=https://goproxy.io ubuntu:golang.12.6 sh -c "go build -ldflags=\"-w -s\" -o app"`
>说明：利用docker打包golang本地项目参数说明：
>`-v` 将本地项目挂在到docker image内部一个路径
>`-w` 切换工作目录
>`-e` 设置环境变量
>`sh -c` 执行打包命令
>`ubuntu:golang.12.6` 是一个具体的docker镜像名称
