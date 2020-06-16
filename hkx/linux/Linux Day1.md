# Linux Day1

## 1.Linux 系统结构目录

![](C:\Users\86138\Desktop\hkx-StudyAccount\hkx\linux\linux-dir-picture1.png)

![](C:\Users\86138\Desktop\hkx-StudyAccount\hkx\linux\linux-dir-picture2.png)

黑色——普通文件（比如自己新建的文件）

蓝色——目录

绿色——可执行文件

浅蓝色——连接文件（该文件会链接到另一个文件）

## 2.文件与目录管理

文件管理

（1）建立空白文件

`touch file` 建立空文件，或修改文件的时间戳

`touch file1 file2` 建立多个文件（file1 file2）

（2）建立文件夹

`mkdir` 建立单目录

`mkdir -p` 建立多层目录

（3）文件夹的删除

`rm file` 删除file文件夹，但是会提示是否删除，选择yes或者no

`rm -f file` 强行删除文件不提示

`rm -fr dir` 强行删除目录本身和里面的内容，不提示



文件编辑

（1）`vim file` 进入file文件编译

进入文件后输入 `i` 进入文件输入模式，可以向文件中输入内容

（2）退出编译模式

按<esc>退出插入编译模式，进入浏览模式

退出编译模式后可以对文本进行复制粘贴功能和批量操作   通过方向键操作光标进行操作

a：字符基本操作命令
yy        复制一整行
yl        复制一个字母
yw       复制一个单词
p         粘贴

dd        删除一整行
dl        删除一个字母
dw       删除一个单词

cc        剪掉整行
cl        剪贴一个字母
cw      剪贴一个单词

u         撤销
ctrl+r   恢复b：批量操作管理

在浏览模式下，输入ctrl + v 进入可视化模式，通过光标选择需要操作的字符所在

按<I>进入插入模式并写入要加入的字符

按<ESC>批量添加结束

：%s/原有字符/修改后字符/g
：1,5s/原有字符/修改后字符/g

（3）文件的退出

在浏览模式下输入：

:q   ##当文件没有做任何修改是可用
:q!   ##当文件修改但不行保存修改时可用
:wq   ##退出保存
:wq!   ##当文件属于自己或用户为root时可用

（4）多个文件同时打开编辑

vim file
:sp file1

光标默认在那个文件中操作的就是那个文件，ctrl+w 按完放开在按上|下可以移动光标所在窗口



文件查看
文件查看常用命令

cat file             输出文件的所有内容

cat -b file         输出文件所有内容并加入行号

less                 分页浏览        在分页浏览下：上|下        向上|向下移动一行              <pgup>|<pgdn>      向上|向下移动一页

/关键字           高亮显示关键字，n向下匹配N向上匹配

q                      退出

tail -n               显示文件的后多少行

head -n           显示文件的前多少行



文件的复制和移动
cp file file222                                文件复制(将文件file复制到file222中）
cp file file222 123/                       复制多个文件（file file222）到目录（123）中
cp -r  file    123/                            复制目录（123）

mv  file file222              重名命
mv  file  123                 移动
mv file   123                移动目录



文件路径

相对路径：（则必须有前提条件，其实在系统底层依然是绝对路径执行，只是用户看到的简略移动）

文件相对当前系统位置的一个名称简写
文件名称省略了当前路径的值
只有当前在此目录中时可以使用
文件名称不以/开头
文件名称会自动在字符前加入'pwd'显示的路径

例由/usr/share/doc 到/usr/share/man下，可以写成cd ../man

绝对路径：由根目录写起，例/usr/share/doc

绝对路径：

是文件在系统中真实的位置
任何时间都可以精确表示一个文件的名称
文件名称以/开头

pwd            显示当前工作目录
cd               切换当前工作目录
cd /mnt       切换到/mnt目录中
cd -             进入当前目录之前所在目录中

cd ~student        进入到student用户家目录

## 3.yum

常用命令

- 1.列出所有可更新的软件清单命令：yum check-update
- 2.更新所有软件命令：yum update
- 3.仅安装指定的软件命令：yum install <package_name>
- 4.仅更新指定的软件命令：yum update <package_name>
- 5.列出所有可安裝的软件清单命令：yum list
- 6.删除软件包命令：yum remove <package_name>
- 7.查找软件包 命令：yum search <keyword>
- 8.清除缓存命令:
  - yum clean packages: 清除缓存目录下的软件包
  - yum clean headers: 清除缓存目录下的 headers
  - yum clean oldheaders: 清除缓存目录下旧的 headers
  - yum clean, yum clean all (= yum clean packages; yum clean oldheaders) :清除缓存目录下的软件包及旧的headers