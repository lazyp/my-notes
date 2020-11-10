#### 配置ssh client
> `.ssh/config` 配置，可以指定登录用那个sshkey文件
```
Host serveralias
HostName serverIp or serverDomain
User  root or other user name
IdentityFile sshkey path
```
> 配置好后登录直接如下命令:
```
  ssh serveralias
```
