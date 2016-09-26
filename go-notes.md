## 编译瘦身
------------------
我们可以通过下面的方法将其变小点：

采用：`go build -ldflags "-s -w"` 这种方式编译。

解释一下参数的意思：

    -ldflags： 表示将后面的参数传给连接器（5/6/8l）
    -s：去掉符号信息
    -w：去掉DWARF调试信息

注意：

-s 去掉符号表（这样panic时，stack trace就没有任何文件名/行号信息了，这等价于普通C/C+=程序被strip的效果）

-w 去掉DWARF调试信息，得到的程序就不能用gdb调试了

两个可以分开使用

## 交叉编译
CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build    
参数解释：
```
    CGO_ENABLED=0 ;//关闭cgo功能
    GOOS=linux;//操作系统，linux/windows/darwin 
    GOARCH=amd64;//操作系统位数，如64位:GOARCH=amd64，32位:GOARCH=386
```
