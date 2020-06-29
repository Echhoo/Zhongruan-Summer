# 环境搭建&JDBC

## 环境搭建（非服务器）
1. JavaSE8
    - - Java
2. Maven - 构建工具 -- jar包管理
    > [download](https://maven.apache.org/download.cgi?Preferred=https%3A%2F%2Fdownloads.apache.org%2F)

    安装思路（非侵入式）

    依赖管理，所需jar包仓库
    - 远程仓库
      - [中央仓库](https://mvnrepository.com)、企业内部网络仓库
    - 本地仓库
      - 本地的一个目录

    描述使用Mysql JDBC
    > central仓库找Mysql驱动Jar的Pom的依赖描述

    安装过程
    1. 解压到指定文件夹 - 作为主目录
    2. 配置Maven(Ant\Gradle)
        1. 系统配置 = 环境变量（主目录、路径path）
        2. 新建MAVEN_HOME环境变量  

            Mac
            ```
            $ vim ~/.bash_profile 

            MAVEN_HOME=/Library/apache-maven-3.6.3
            export PATH=$PATH:$MAVEN_HOME/bin

            $ source ~/.bash_profile 
            $ mvn -v
            ```
        3. 修改Maven默认的本地仓库

            编辑修改Maven主目录下的./conf/settings.xml
        4. 修改Maven的镜像源

            编辑修改Maven主目录下的./conf/settings.xml
            1. 在settings.xml ~~推荐~~
            2. 在pom.xml

            ```xml
            <mirror>
                <id>aliyunmaven</id>
                <mirrorOf>central</mirrorOf>
                <name>aliyun maven</name>
                <url>http://maven.aliyun.com/nexus/content/groups/public</url>
            </mirror>
            ```
        
        5. 整合配置 - e.g.与IDE整合
        6. 百度自定义Maven骨架

3. IntelliJ IDEA\Eclipse\Vim
    1. Eclipse | Maven
        preference -> maven -> installation -> add external
    2. IntelliJ IDEA
        ~~[idea.lanyus.com](https://idea.lanyus.com)~~
        1. 配置Maven支持
        2. 新建Maven项目[maven](https://repo1.maven.org/maven2/)
        3. IDEA创建纯净Maven项目