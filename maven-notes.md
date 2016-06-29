#### 基础命令
* mvn compile 编译源代码
* mvn test-compile 编译unit测试代码
* mvn install 编译并且打包
* mvn install -Dmaven.test.skip=true 编译并且打包,以及不执行junit
* mvn clean 清理
* mvn deploy 发布项目到仓库

###### mvn dependency:copy-dependencies 命令 ########
1. 进入pom.xml目录下执行: ```mvn dependency:copy-dependencies```,会把所有依赖包拷贝到`target/dependency`目录下   
2. 自定义jar的输出目录,执行```mvn dependency:copy-dependencies -DoutputDirectory=dir```,会把所有依赖包拷贝到指定的目录dir下面    
3. ```mvn dependency:copy-dependencies -DoutputDirectory=lib   -DincludeScope=compile```,指定需要的依赖级别`scope`   
