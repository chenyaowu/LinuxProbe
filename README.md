# LinuxProbe
# 第2章-新手必须掌握的 Linux 命令 



## 常用系统工作命令



### 1.echo命令

- echo 命令用于在终端输出字符串或变量提取后的值，格式为“echo [字符串 | $变量]”。

  ```bash
  [root@linuxprobe ~]# echo Linuxprobe.Com
  Linuxprobe.Com
  [root@linuxprobe ~]# echo $SHELL
  /bin/bash
  ```

### 2.date命令

- date 命令用于显示及设置系统的时间或日期，格式为“date [选项] [+指定的格式]”。

  | 参数 | 作用           |
  | ---- | -------------- |
  | %t   | 跳格[Tab键]    |
  | %H   | 小时(00~23)    |
  | %I   | 小时(00~12)    |
  | %M   | 分钟(00~59)    |
  | %s   | 秒(00~59)      |
  | %j   | 今年中的第几天 |

  ```ba
  按照默认格式查看当前系统时间
  [root@linuxprobe ~]# date
  Mon Aug 24 16:11:23 CST 2017 
  按照“年-月-日 小时:分钟:秒”的格式查看当前系统时间
  [root@linuxprobe ~]# date "+%Y-%m-%d %H:%M:%S"
  2017-08-24 16:29:12 
  设置时间
  [root@linuxprobe ~]# date -s "20170901 8:30:00"
  Fri Sep 1 08:30:00 CST 2017 
  查看今天是当年中的第几天
  [root@linuxprobe ~]# date "+%j" 
  244
  ```

### 3.reboot命令

- reboot 命令用于重启系统

### 4.poweroff 命令

- poweroff 命令用于关闭系统

### 5.wget 命令

- wget 命令用于在终端中下载网络文件，格式为“wget [参数] 下载地址”。

  | 参数 | 作用                               |
  | ---- | ---------------------------------- |
  | -b   | 后台下载模式                       |
  | -P   | 下载到指定目录                     |
  | -t   | 最大尝试次数                       |
  | -c   | 断点续传                           |
  | -p   | 下载页面所有资源，包括图片、视频等 |
  | -r   | 递归下载                           |

  

### 6.ps命令

- ps 命令用于查看系统中的进程状态，格式为“ps [参数]”。

  | 参数 | 作用                               |
  | ---- | ---------------------------------- |
  | -a   | 显示所有进程（包括其他用户的进程） |
  | -u   | 用户以及其他详细信息               |
  | -x   | 显示没有控制终端的进程             |

- 5种常见的进程状态

  - R（运行）：进程正在运行或在运行队列中等待。 
  -  S（中断）：进程处于休眠中，当某个条件形成后或者接收到信号时，则脱离该 状态。 
  - D（不可中断）：进程不响应系统异步信号，即便用 kill 命令也不能将其中断。 
  - Z（僵死）：进程已经终止，但进程描述符依然存在, 直到父进程调用 wait4()系统函数 后将进程释放。 
  - T（停止）：进程收到停止信号后停止运行。

- ps输出信息

  | USER         | PID      | %CPU         | %MEM       | VSZ                  | RSS                    | TTY        | STAT     | START        | TIME              | COMMAND          |
  | ------------ | -------- | ------------ | ---------- | -------------------- | ---------------------- | ---------- | -------- | ------------ | ----------------- | ---------------- |
  | 进程的所有者 | 进程ID号 | 运算器占用率 | 内存占用率 | 虚拟内存使用量（KB） | 占用的固定内存量（KB） | 所在的终端 | 进程状态 | 被启动的时间 | 实际使用CPU的时间 | 命令名称与参数   |
  | root         | 1        | 0.0          | 0.14       | 53684                | 7628                   | ?          | Ss       | 07:00        | 0:22              | /usr/lib/systemd |

### 7.top 命令

- top 命令用于动态地监视进程活动与系统负载等信息
  - 第 1 行：系统时间、运行时间、登录终端数、系统负载（三个数值分别为 1 分钟、5 分钟、15 分钟内的平均值，数值越小意味着负载越低）。 
  - 第 2 行：进程总数、运行中的进程数、睡眠中的进程数、停止的进程数、僵死的进程 数。 
  - 第 3 行：用户占用资源百分比、系统内核占用资源百分比、改变过优先级的进程资源 百分比、空闲的资源百分比等。(数据均为 CPU 数据并以百分比格式显示，例如“97.1 id”意味着有 97.1% 的 CPU 处理器资源处于空闲。)
  - 第 4 行：物理内存总量、内存使用量、内存空闲量、作为内核缓存的内存量。 
  - 第 5 行：虚拟内存总量、虚拟内存使用量、虚拟内存空闲量、已被提前加载的内存量。

### 8.pidof 命令 

- pidof 命令用于查询某个指定服务进程的 PID 值，格式为“pidof [参数] [服务名称]”。

  ```ba
  [root@linuxprobe ~]# pidof sshd
  2156 
  ```

### 9.kill 命令

- kill 命令用于终止某个指定 PID 的服务进程，格式为“kill [参数] [进程 PID]”。

### 10.killall 命令

 - killall 命令用于终止某个指定名称的服务所对应的全部进程，格式为：“killall [参数] [进 程名称]”。



 ## 系统状态检测命令 

### 1.ifconfig 命令

- ifconfig 命令用于获取网卡配置与网络状态等信息，格式为“ifconfig [网络设备] [参数]”。

### 2.uname 命令 

- uname 命令用于查看系统内核与系统版本等信息，格式为“uname [-a]”。

### 3.uptime 命令

- uptime 用于查看系统的负载信息，格式为 uptime

### 4.free 命令

- free 用于显示当前系统中内存的使用量信息，格式为“free [-h]”。

  |                  | 内存总量 | 已用量 | 可用量 | 进程共享的内存量 | 磁盘缓存的内存量 | 缓存的内存量 |
  | ---------------- | -------- | ------ | ------ | ---------------- | ---------------- | ------------ |
  |                  | total    | used   | free   | shared           | buffers          | cached       |
  | Mem              | 1.8GB    | 1.3GB  | 542MB  | 9.8MB            | 1.6MB            | 413MB        |
  | -/+buffers/cache |          | 869MB  | 957MB  |                  |                  |              |
  | Swap             | 2.0GB    | 0      | 2.0GB  |                  |                  |              |

### 5.who 命令

- who 用于查看当前登入主机的用户终端信息，格式为“who [参数]”。

  | 登录的用户名 | 终端设备 | 登录到系统的时间     |
  | ------------ | -------- | -------------------- |
  | root         | :0       | 2017-08-24 17:52(:0) |
  | root         | pts/0    | 2017-08-24 17:52(:0) |

### 6.last 命令

- last 命令用于查看所有系统的登录记录，格式为“last [参数]”。

### 7.history 命令 

- history 命令用于显示历史执行过的命令，格式为“history [-c]”。

### 8.sosreport 命令 

- sosreport 命令用于收集系统配置及架构信息并输出诊断文档，格式为 sosreport。

## 工作目录切换命令 

### 1.pwd 命令

- pwd 命令用于显示用户当前所处的工作目录，格式为“pwd [选项]”。

### 2.cd 命令

- cd 命令用于切换工作路径，格式为“cd [目录名称]”。

### 3.ls 命令

- ls 命令用于显示目录中的文件信息，格式为“ls [选项] [文件] ”。
  - “-a”参数看 到全部文件（包括隐藏文件）。
  - “-l”参数可以查看文件的属性、大小等详细信息。
  - “-d”参数查看目录属性信息

## 文本文件编辑命令 

### 1.cat 命令

- cat 命令用于查看纯文本文件（内容较少的），格式为“cat [选项] [文件]”。
  - 显示行号加-n参数

### 2.more 命令

- more 命令用于查看纯文本文件（内容较多的），格式为“more [选项]文件”。
  - 使用空格键或回 车键向下翻页

### 3.head 命令

- head 命令用于查看纯文本文档的前 N 行，格式为“head [选项] [文件]”。

### 4.tail 命令

- tail 命令用于查看纯文本文档的后 N 行或持续刷新内容，格式为“tail [选项] [文件]”。

  ```bash
  查看最后20行
  [root@linuxprobe ~]# tail -n 20 /var/log/messages 
  ```

### 5. tr 命令

- tr 命令用于替换文本文件中的字符，格式为“tr [原始字符] [目标字符]”。

### 6.wc 命令

- wc 命令用于统计指定文本的行数、字数、字节数，格式为“wc [参数] 文本”。

  | 参数 | 作用         |
  | ---- | ------------ |
  | -l   | 只显示行数   |
  | -w   | 只显示单词数 |
  | -c   | 只显示字节数 |

### 7.stat 命令 

- stat 命令用于查看文件的具体存储信息和时间等信息，格式为“stat 文件名称”。

### 8.cut 命令

- cut 命令用于按“列”提取文本字符，格式为“cut [参数] 文本”。

### 9.diff 命令

- diff 命令用于比较多个文本文件的差异，格式为“diff [参数] 文件”。

## 文件目录管理命令

### 1.touch 命令

- touch 命令用于创建空白文件或设置文件的时间，格式为“touch [选项] [文件]”。

  | 参数 | 作用                    |
  | ---- | ----------------------- |
  | -a   | 仅修改“读取时间”(atime) |
  | -m   | 仅修改“修改时间”(mtime) |
  | -d   | 同时修改atime与mtime    |

### 2.mkdir 命令

- mkdir 命令用于创建空白的目录，格式为“mkdir [选项] 目录”。

  ```bash
  使用-p递归创建层级关系目录
  [root@linuxprobe linuxprobe]# mkdir -p a/b/c/d/e 
  ```

### 3.cp 命令 

- cp 命令用于复制文件或目录，格式为“cp [选项] 源文件 目标文件”。

  - 如果目标文件是目录，则会把源文件复制到该目录中；

  - 如果目标文件也是普通文件，则会询问是否要覆盖它；

  - 如果目标文件不存在，则执行正常的复制操作。

    | 参数 | 作用                                         |
    | ---- | -------------------------------------------- |
    | -p   | 保留原始文件的属性                           |
    | -d   | 若对象为“链接文件”，则保留该“链接文件”的属性 |
    | -r   | 递归持续复制（用于目录）                     |
    | -i   | 若目标文件存在则询问是否覆盖                 |
    | -a   | 相当于-pdr（p、d、r 为上述参数）             |

### 4.mv 命令

- mv 命令用于剪切文件或将文件重命名，格式为“mv [选项] 源文件 [目标路径|目标文件名]”。

### 5.rm 命令

- rm 命令用于删除文件或目录，格式为“rm [选项] 文件”。

### 6. dd 命令

- dd 命令用于按照指定大小和个数的数据块来复制文件或转换文件，格式为“dd [参数]”。

### 7.file 命令

- file 命令用于查看文件的类型，格式为“file 文件名”。

## 打包压缩与搜索命令

### 1.tar 命令

- tar 命令用于对文件进行打包压缩或解压，格式为“tar [选项] [文件]”。

  | 参数 | 作用                   |
  | ---- | ---------------------- |
  | -c   | 创建压缩文件           |
  | -x   | 解开压缩文件           |
  | -t   | 查看压缩包内有哪些文件 |
  | -z   | 用 Gzip 压缩或解压     |
  | -j   | 用 bzip2 压缩或解压    |
  | -v   | 显示压缩或解压的过程   |
  | -f   | 目标文件名             |
  | -p   | 保留原始的权限与属性   |
  | -P   | 使用绝对路径来压缩     |
  | -C   | 指定解压到的目录       |

### 2.grep 命令 

- grep 命令用于在文本中执行关键词搜索，并显示匹配的结果，格式为“grep [选项] [文件]”。

  | 参数 | 作用                                             |
  | ---- | ------------------------------------------------ |
  | -b   | 将可执行文件（binary）当作文本文件（text）来搜索 |
  | -c   | 仅显示找到的行数                                 |
  | -i   | 忽略大小写                                       |
  | -n   | 显示行号                                         |
  | -v   | 反向选择—仅列出没有“关键词”的行                  |

### 3.find 命令

- find 命令用于按照指定条件来查找文件，格式为“find [查找路径] 寻找条件 操作”。

  | 参数               | 作用                                                         |
  | ------------------ | ------------------------------------------------------------ |
  | -name              | 匹配名称                                                     |
  | -perm              | 匹配权限（mode 为完全匹配，-mode 为包含即可                  |
  | -user              | 匹配所有者                                                   |
  | -group             | 匹配所有组                                                   |
  | -mtime -n +n       | 匹配修改内容的时间（-n 指 n 天以内，+n 指 n 天以前）         |
  | -atime -n +n       | 匹配访问文件的时间（-n 指 n 天以内，+n 指 n 天以前）         |
  | -ctime -n +n       | 匹配修改文件权限的时间（-n 指 n 天以内，+n 指 n 天以前）     |
  | -nouser            | 匹配无所有者的文件                                           |
  | -nogroup           | 匹配无所有组的文件                                           |
  | -newer f1 !f2      | 匹配比文件 f1 新但比 f2 旧的文件                             |
  | --type b/d/c/p/l/f | 匹配文件类型（后面的字幕参数依次表示块设备、目录、字符设备、管道、 链接文件、文本文件） |
  | -size              | 匹配文件的大小（+50KB 为查找超过 50KB 的文件，而-50KB 为查找小于 50KB 的文件） |
  | -prune             | 忽略某个目录                                                 |
  | -exec …… {}\;      | 后面可跟用于进一步处理搜索结果的命令                         |

  

# 第3章管道符、重定向与环境变量

## 输入输出重定向

- 输入重定向是指把文件导入到命令中，而输出重定向则是指把原本要输出到 屏幕的数据信息写入到指定文件中

- 标准输入重定向（STDIN，文件描述符为 0）：默认从键盘输入，也可从其他文件或命令中输入

- 标准输出重定向（STDOUT，文件描述符为 1）：默认输出到屏幕。

- 错误输出重定向（STDERR，文件描述符为 2）：默认输出到屏幕。

- 输入重定向中用到的符号及其作用

  | 符号                   | 作用                                            |
  | ---------------------- | ----------------------------------------------- |
  | 命令 < 文件            | 将文件作为命令的标准输入                        |
  | 命令 << 分界符         | 从标准输入中读入，直到遇见分界符才停止          |
  | 命令 < 文件 1 > 文件 2 | 将文件 1 作为命令的标准输入并将标准输出到文件 2 |

  

- 输出重定向中用到的符号及其作用

  - 对于重定向中的标准输出模式，可以省略文件描述符 1 不写，而错误输出模式的文件描述符 2 是必须要写的。

  | 符号                               | 作用                                                         |
  | ---------------------------------- | ------------------------------------------------------------ |
  | 命令 > 文件                        | 将标准输出重定向到一个文件中（清空原有文件的数据）           |
  | 命令 2> 文件                       | 将错误输出重定向到一个文件中（清空原有文件的数据）           |
  | 命令 >> 文件                       | 将标准输出重定向到一个文件中（追加到原有内容的后面）         |
  | 命令 2>> 文件                      | 将错误输出重定向到一个文件中（追加到原有内容的后面）         |
  | 命令 >> 文件 2>&1 或 命令 &>> 文件 | 将标准输出与错误输出共同写入到文件中（追加到原有内容的 后面） |

## 管道命令符

- 格式 命令 A | 命令 B |

- 把前一个命令原本要输出到屏幕的数据当作是后一个命令的标准输 入

## 命令行的通配符 

- 星号（*）代 表匹配零个或多个字符
- 问号（?）代表匹配单个字符
- 中括号内加上数字[0-9]代表匹配 0～9 之间的单个数字的字符
- 中括号内加上字母[abc]则是代表匹配 a、b、c 三个字符中的任意 一个字符。

## 常用的转义字符 

- 反斜杠（\）：使反斜杠后面的一个变量变为单纯的字符串。
- 单引号（''）：转义其中所有的变量为单纯的字符串。
- 双引号（""）：保留其中的变量属性，不进行转义处理。
- 反引号（``）：把其中的命令执行后返回结果。

## 重要的环境变量 

- 在用 户执行了一条命令之后，分别执行4个步骤

  - 第1步：判断用户是否以绝对路径或相对路径的方式输入命令（如/bin/ls），如果是的话 则直接执行。
  - 第2步：Linux 系统检查用户输入的命令是否为“别名命令”，即用一个自定义的命令 名称来替换原本的命令名称。可以用 alias 命令来创建一个属于自己的命令别名，格式为 “alias 别名=命令”。若要取消一个命令别名，则是用 unalias 命令，格式为“unalias 别名”。 
  - 第3步：Bash 解释器判断用户输入的是内部命令还是外部命令。内部命令是解释器内部 的指令，会被直接执行；而用户在绝大部分时间输入的是外部命令，这些命令交由步骤 4 继 续处理。可以使用“type 命令名称”来判断用户输入的命令是内部命令还是外部命令。
  - 第4步：系统在多个路径中查找用户输入的命令文件，而定义这些路径的变量叫作 PATH，可 以简单地把它理解成是“解释器的小助手”，作用是告诉 Bash 解释器待执行的命令可能存放 的位置，然后 Bash 解释器就会乖乖地在这些位置中逐个查找。PATH 是由多个路径值组成的 变量，每个路径值之间用冒号间隔，对这些路径的增加和删除操作将影响到 Bash 解释器对 Linux 命令的查找。

- 为什么不能将当前目录（.）添加到 PATH 中呢? 

  - 尽管可以将当前目录（.）添加到 PATH 变量中，从而在某些情况下可以让用户免去输入命令 所在路径的麻烦。但是，如果黑客在比较常用的公共目录/tmp 中存放了一个与 ls 或 cd 命令同 名的木马文件，而用户又恰巧在公共目录中执行了这些命令，那么就极有可能中招了。

- Linux 系统中最重要的 10 个环境变量

  | 变量名称     | 作用                             |
  | ------------ | -------------------------------- |
  | HOME         | 用户的主目录（即家目录）         |
  | SHELL        | 用户在使用的 Shell 解释器名称    |
  | HISTSIZE     | 输出的历史命令记录条数           |
  | HISTFILESIZE | 保存的历史命令记录条数           |
  | MAIL         | 邮件保存路径                     |
  | LANG         | 系统语言、语系名称               |
  | RANDOM       | 生成一个随机数字                 |
  | PS1          | Bash 解释器的提示符              |
  | PATH         | 定义解释器搜索用户执行命令的路径 |
  | EDITOR       | 用户默认的文本编辑器             |

  

