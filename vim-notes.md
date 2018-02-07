####基础
安装vim:  
Ubuntu/Debian:   
> sudo apt-get install vim   

RedHat/Centos:   
> sudo yum install vim    

<hr>
#### 命令模式和编辑模式切换   
1. vim file_name 打开一个文件,打开后默认处于vim命令模式,可按 **i** 在当前位置插入数据 或者 **o** 下一行位置开始插入数据,来进入编辑模式.     
2. 在编辑模式下,按`esc`进入命令模式.  

<hr>
#### 进入块编辑
在`vim`命令编辑模式下输入 `ctrl+v` 进入列编辑模式

#### 在同一个vim中打开多个文件编辑 ####
* 打开多个文件方法一 : ```vim file1.txt file2.txt file3.txt```
* 打开多个文件方法二 : 在<code>vim</code>已经打开的状态下,按```esc```进入命令模式,然后输入```:open file.txt```
* 多个文件间切换,按```esc```进入命令模式,然后输入
```
     :bn—下一个文件
     :bp—上一个文件 
```
* ```:ls```可以查看当前打开的文件列表

####在同一个vim分屏显示多个文件同时编辑###
* vim分屏可以用如下两个命令
```
    :split    简写  :sp   #上下分屏
    :vsplit  简写  :vsp  #左右分屏
```
* 多个子窗口间切换```Ctrl+ww``` 依次向后切换到下一个窗格中

#### 在vim输入以下命令就可以格式化json内容
`
:%!python -m json.tool

> 可以在~/.vimrc增加快捷键
> map <F4> <Esc>:%!python -m json.tool<CR>

`
