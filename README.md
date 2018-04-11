# Q&A for PA2018 NUAA
PA2018常见问题解答（持续更新，更新频率1-2天/次），欢迎star
------
# 读前必看

1.提问以前务必翻看翻看本问答文档，对于文档中已经给出的问题，不再回复，敬请谅解！！

2.有偿（`1分钱QQ红包`）征集你们遇到的问题的解决办法
想分享你遇到问题的解决办法？没问题你可以把想说的话，想提醒大家的事情，还包括代码框架本身的bug等等`直接以Pull Requests的形式`提交到本仓库的`Master`分支，遇到有人提交我会上去检查一下后合并的。另外这个问答的issue功能关掉了，以免有人使用不文明用语或发答案。

3.注意这里不是给你共享答案的地方，后面每周检查报告的时候是有查重的，请你们珍惜自己的代码……因此遇到这种提交不予合并，技术性难题你们可以一起讨论。温馨提醒：每次你们提交的报告都会**查重**，请不要把自己的代码分享给别人，遇到雷同的估计可能会被**算没交**

4.新添加的问题将放在最前面，以免你们看不到以为没更新，想看历史比较久远的问题往后面看

5.为了鼓励大家提前做，以及分散提问人流，我们采取这个策略：本次报告`截止时间前24小时内`，仅在`14:00-16:00`，`22:00-23:59`集中回复两次；截止时间24小时之前，随问随答（当然是看到了消息的时候，如果逢在上课只有抱歉了……）。请留意。

## 最后更新日期：2018.4.5

# PA2

* 2018.4.11更新：

5.实现jcc相关指令时（jbe,jle），一定要记得先看讲义的勘误表。。。。。

补充说明：其实为方便大家查看，大部分勘误已在PDF文档上直接标出，如果同学们的阅读器看不到这些标记，请使用`Adobe PDF Reader`或`Adobe Acrobat`这两款PDF阅读器查看，另，真心推荐大家写文档，看文档不要使用`WPS文字`系列，不是不支持国产，是它确实很多功能不行，如果你是`Linux`桌面，我反而会强烈推荐你使用`WPS文字`系列。

* 2018.3.29更新：

4.在执行命令：
``` bash
make ARCH=x86-nemu ALL=dummy run
```
时遇到找不到头文件`<bits/libc-header-start.h>`或其他头文件错误时，多半是没有安装软件包`g++-multilib`，请使用命令
``` bash
apt-get install g++-multilib
```
来安装，另，之前有部分虚拟机同学按照老版讲义在做，这里有一个遗留问题，那就是**安装的组件是老版PA的组件，新版的PA组件没有安装，请参考讲义PDF第16页**，确认自己安装了如下软件包：
``` bash
apt-get install build-essential
apt-get install gdb
apt-get install git
apt-get install libreadline-dev
apt-get install libsdl2-dev
### 以上几个相信经过了PA0和PA1就算没装的也都补上了，那么下面这个记得装一下 ###
apt-get install qemu-system-x86  # QEMU
```

* 2018.3.1更新:

3.神奇的一点，GitHub 上添加代码名称时需要在 ` ``` ` 后添加空格，否则不会显示代码高亮。不过现在流行的桌面编辑器貌似都不添加空格。

2.如果遇到找不到`sys/cdefs.h`的问题，可以通过安装`gcc-multilib`包解决。

1.遇到问题:
``` bash
make ARCH=x86-nemu ALL=dummy run
Makefile:1:  /Makefile.check: No such file or directory.
```
你可以先试着添加环境变量：
``` bash
export AM_HOME=/home/your name/ics2017/nexus-am
```
然后你再跑一次，发现会出现：
``` bash
make ARCH=x86-nemu ALL=dummy run
Building am [x86-nemu]
make[2] *** No targets specified and no makefile found
...
```
如果遇到，检查`~/.bashrc`目录，是否存在
``` bash
export NEMU_HOME=/home/your name/ics2017/nemu
export AM_HOME=/home/your name/ics2017/nexus-am
export NAVY_HOME=/home/your name/ics2017/navy-apps
```
三个变量
这个问题出现的原因可能是修改了环境（我是把 bash 改成了 zsh）。所以尽量在 PA0 之后就不要再修改环境了。

# PA1

* 2018.3.28更新：

17.出现错误
``` bash
regex compliation failed
```
的原因是`你的正则表达式有一个（或多个）写的有问题，导致初始化NEMU失败`，而非你修改了框架的初始化函数（如果你修改了，那就没救了）或框架写的有问题，请检查你的正则表达式，如果不会请重新学习`正则表达式`，给大家推荐一个简单的正则表达式入门教程，地址：[http://deerchao.net/tutorials/regex/regex.htm](http://deerchao.net/tutorials/regex/regex.htm)，只需要15分钟，从头看到“分枝条件”结束即可。

16.温馨提醒：**不要去修改讲义或课上中没有提到让修改的框架代码**，不要修改的部分无非是`有明显注释告诉你不要修改这里`或者`某个函数或模块已经写的非常完整了，完全没有必要修改`两种情况。修改框架后果自负，此类作死不予解决问题，只能建议回滚代码。

* 2018.3.26更新：

15.PA1的内容都是实现调试器功能，输出什么当然可以根据自身情况而定，当然为了以后能做的更方便（如果还有以后的话，当然作者还是希望诸君有以后……），还是能多实现完整一点就完整一点吧。

14.有同学问监视点要输出什么，可以参考`gdb`的`info w`的输出情况，下面还是给个参考输出（**不需要完全一样**）：
```bash
(nemu) info w
Num Type Value      Enb What
1   w    0x1234     y   $eax
2   b    0x0        y   $eip==0x100020
3   w    0x234      n   0x123+0x111
```
其中，各个字段意义如下：
```
Num   监视点（断点）编号
Type  监视点/断点
Value 表达式的当前计算值
Enb   监视点（断点）是否开启
What  被监视的表达式
```
其中，`Type`字段为`w`的是监视点，为`b`的是断点。
其中，`Enb`字段为`y`的是开启状态（yes），为`n`的是关闭状态（no）。（这个好像没强制要做，自己看着办吧）

13.有同学问报告要写什么，给个大概思路吧：
- 代码：顾名思义
- 执行截图：顾名思义，至少让人知道你的代码能否正常执行
- 编写思路：代码为啥会这样写的一段文字描述，这个很必要也很重要
- 思考题：顾名思义，一句话能说明可以不用两句，但一定要有，不要偷懒
- Git Log：顾名思义

如果可以的话还可以谈谈原理等等。

* 2018.3.8更新：

12.关于第10条，补充一个快速鉴别自己是否做对的方法，首先用命令
```bash
(nemu) x 10 0x100000
```
得到NEMU地址0x100000起始的若干字节内存信息，然后使用命令
```bash
(nemu) si 5
```
运行测试程序，观察执行的反汇编序列与`x`扫描内存命令得到的结果是否一致。若一致，则实现正常。

* 2018.3.6更新：

11.（3.9修改）有同学反映使用`git commit`命令提示代码无修改，操作被git拒绝，原因是没有加上`--allow-empty`参数，其原因是你每次`make`或`make run`的时候，你的修改就被自动记录了，所以你**不使用上述参数的话git就不允许空更改**，所以提交更改失败。所以提交更改请使用命令：
```bash
git commit --allow-empty
```
然后就有同学觉得：`那既然每次编译和运行都自动提交更改了，为什么还需要我们自己commit呢？`这个问题从若干方面来看：
- 空提交是你为了**标记你自己做到哪里的里程碑**，你自己的提交是为了给当前的进度标记一个醒目的标识。
- 自己commit**可以附带一句话描述**，而千篇一律的`run`和`compile`记录**并不能准确描述当前做到哪里了**，因此如果到时候你想回转代码，并不知道应该跳转到哪里
- 自动记录到期末可能有3k-4k条（对于到那个时候还没放弃的同学），而自己的提交记录通常不会超过0.3k条，因此对于期末检查git log记录来说也很方便，也方便你们**平时报告上截取git log的截图**

10.关于扫描内存命令，想知道自己做的对不对很简单，把用户程序用`objdump工具`反汇编一下，然后对比反汇编代码就知道是否正确了。从经验的角度建议大家把每个4字节十六进制数在同一行把单字节序列形式也显示出来，**今后请务必注意大小端问题**。参考输出（不需要一样）：
```bash
(nemu) x 4 0x100000
Address    Big-Endian ... Little-Endian
0x00100000 0x000000b8 ... b8 00 00 00
0x00100004 0x0000bb00 ... 00 bb 00 00
0x00100008 0x00b90000 ... 00 00 b9 00
0x0010000c 0xba000000 ... 00 00 00 ba
```
当然只是条建议，方便今后看程序的反汇编，当然这条只是经验建议，可以不理睬。

* 2018.3.5更新：

9.**报告既要有截图，又要有文字说明**，如果全是截图没有说明的话很难知道你这一步在做什么。**截图请走心**，不要弄个糊的不行的图贴到对话框里发过来，根本看不清写的啥。

8.有同学反映在马里奥的路径下使用`make run`命令后，没有出现任何画面，命令行仿佛假死了。其实不然，你要是输什么字符还是会显示出来的，但是没有意义。没有出现画面有以下几种原因：
  - **直接在虚拟机里运行**。这种情况请参考搭建X11环境，并使用`Putty`连接，同时记得打开`Xming`；
  - X11配置不对。这种情况请自行检查是哪一步搭建做的有问题。无法显示画面的问题如果这里马里奥解决不了，但是由于到**本课程中期以后会一定需要显示画面**，所以不想重修的同学请务必在当前任务较轻的阶段就把这个问题解决掉。

7.不要去修改PA的目录名字`ics2017`，否则后续会出现莫名其妙的错误，很难修复，已经改了名字的同学建议重新获取（`git clone`）项目

* 2018.3.3更新：

6.80386开发文档（400多页的那个PDF文档）的正确打开方式是当作一本**字典**来查询，PDF阅读器一般都带有目录索引功能，大家可在索引里面找到自己想看的章节或小节进行查询（你的PDF阅读器out了没有索引功能？推荐使用最新版的`Adobe Acrobat`或`Adobe Reader`），`而不是当作小说来阅读`，不要被打开第一眼看到的页码和密密麻麻的文字吓着了，其中的英文都是简单句，一般过了四级都能够看得懂。

5.单步执行的`si`命令，推荐自行检查以下几个测试用例要正确通过：`si`、`si -1`、`si 10`、`si 15`、`si 1`。

4.**使用Putty+Xming的同学请忽略本条。** 如果有同学使用`Xshell+Xmanager`连接Linux主机出现X11转发失败，导致无法显示图形界面，这个问题已经得知，目前该问题仅出现在非debian的linux系统上（如CentOS），具体解决方案请期待后续更新。

* 2018.3.1更新：

3.有同学问怎么RTFSC，我的回答是从`main函数`开始，后面你就懂了。

2.验证自己的结构体（或联合体）是否写对了：运行项目，不出现`assert failure`就是写对了，其原理是生成几个随机数赋给寄存器，然后从里面再读出来，验证写的和读的是否一样，具体请RTFSC。

1.有同学问，我连寄存器的组织结构都不知道，怎么让我写结构体？问这个问题的同学**纯属不读讲义**，各通用寄存器的组织关系在讲义里写的非常清楚

# PA0

* 2018.3.3更新：

38.遇到问题报错请仔细阅读出错提示，虽然是英文，但我保证你能够理解那些英文提示信息说的什么意思，很多情况下读完给出的英文报错信息就能解决问题，你截图给我我也只能帮你人工翻译，如果遇到语言问题，请点击[这里](https://translate.google.cn/)，另外，请从日常开始把英文学好。

37.还有同学在配置docker？？一方面请这些同学加快进度，另一方面，发现很多同学对照这本文档第四条操作还是有误，问题出在并没有仔细阅读本文档，**将daemon.json放到了错误的地方**，导致看似换了好几个地方的源，还是失败，结果错误提示还显示从docker.io这个国外网站获取失败。如果认为自己解决不了，务必在提问时附上你的**daemon.json的文件内容**和**daemon.json的文件属性（即右键->属性）**

* 2018.3.1更新：

36.关于有同学到宿舍死活docker拉取不了镜像：给你一个寒假在家做就是为了拖到学校用学校的烂网做的吗？有同学说不啊我觉得宿舍网络比家里快，应该要好一些，还有这种想法的同学可以参见问答`第32条`。

35.关于git log记录，编译（`make`命令）几次就应该有几个`compile`的log项，执行（`make run`命令）几次就应该有几个`run`的log项，而自己commit的项（即作者为`user.name`里设置的）则是需要你使用`git commit --allowempty`命令提交的更改（查询时可使用`git log user='xxx'`，其中xxx是`user.name`）。

34.有虚拟机同学反映`standard system utilities`无法安装，跳过后没有sudo，这里给大家列出这个标准系统组件中含有的包（需要哪个安装哪个，比如`sudo`，`ifconfig`等等）：[http://bbs.chinaunix.net/thread-1924206-1-1.html](http://bbs.chinaunix.net/thread-1924206-1-1.html) 请看链接的五楼回答。另外这个方法不能保证后面和正常安装的同学一模一样不会出问题，到时候出了问题再解决就好了，所以平时注意保存你们的代码（推荐申请一个代码仓库来，现在国内的[码云](http://git.oschina.net/)蛮火的，而且免费建私有项目，不妨试试）

* 2018.2.28更新：

33.**能在手册上查到的东西尽量自己查手册**（如指令的操作和含义等啦，GDB/GCC的使用方法和那些参数的意义啦，docker的这些命令参数啦，Linux的指令和参数啦，某某库里有哪些函数啦），我这又不是机器人，你问我我也是去查手册，何必一定要搬运一次呢

32.与课程无关，科普一个概念：**网络环境好≠网速很快**。有人说宿舍网络快就是网络环境好，实则不然，网络环境的要素很多，如果有玩P2P（BitTorrent,Emule,Share,....）的同学应该知道一个High/Low ID的概念，实际上你们不更换源从国外下载，更是经过多少次的转发，一般来说ISP给家庭用户是能够达到给公网IP的开放程度的（有些为了节省IP采用NAT，都不是很影响），但是宿舍的网首先就和家庭网不太一样，架构不同，甚至被所谓“客户端”绑架，导致网络环境很差，跑测试都不是很好用，说这么多只想证明一点，在家不做的回学校做这个更难做

31.找不到SDL2/SDL.h的问题，参考链接：[http://blog.csdn.net/hank12580/article/details/45949995 ](http://blog.csdn.net/hank12580/article/details/45949995)

30.（还有几天就截止了还有人在装虚拟机，进度要加快了啊）安装完虚拟机后马上开机，可能又进入安装界面，因此请大家安装成功后关闭虚拟机，然后调整**开机的引导顺序，将硬盘调整至光驱之前**，再开机

29.请**一个一个字读讲义**，如果条件允许建议**一边朗读一边做**，以免有些人讲义上写的明明白白的黑底白字就是没看到，让人感到上帝为何要赐予你被蒙蔽着的双眼

28.你们都20左右不小了，应该知道做什么都没有一帆风顺的，遇到问题首先应该**学会自己解决**，把能查的（`官方文档/手册`、`搜索引擎`、`在线近期问题汇总`）都查了，解决不了的再说（当了二十年的**网虫**就是当**伸手党**的吗？）

* 2018.2.27更新：

27.如果遇到`gdb`出现问题：
``` bash
warning: Error disabling address space randomization: Operation not permited
```
可能是由于 docker 默认开启了 ASLR(Address space layout randomization) 。
我的解决方法是重新配置容器，在执行`create`命令时加入`--privileged`参数即可。
另外，PA 实验并没有必要使用 gdb 。

26.`PA`是`组成原理课程设计`，是独立于组成原理课的单独的一门课，1个学分，挂了没有补考，按目前行情重修100元；组成原理实验0.5个学分，同样挂了没补考，重修50元，如果内容和去年相同的话那就是ICS Lab的前两个实验，这个具体后面老师会布置的，现在暂时不用管

25.关于有同学dockerfile中没把用户名密码替代成自己的问题：修改用户名用命令`sudo usermod –l 新名字 旧名字`，修改密码命令自己网上查一下吧很简单（关键词：【`Linux 修改密码`】），这个注意一下，为了确保检查报告的时候看你的图是不是自己做的而不是盗图，所以请务必把debian的用户名设成自己的真名拼音（不一定非要全名拼音，简写QQ啥的都可以，只要能认得出你就OK），这个将作为抄袭检查的依据之一（这个作为建议，只要能让人看出来是你自己做的就行，对于已经做完的，**就在报告末尾加一句，我改名啦就行了**，而且**造成这个问题的本来原因就是你们在生成容器的时候不仔细看讲义没有修改那个用户名参数**，无可非议）

24.补充之前说的建议装32位系统：64位也可以，只要能成功编译拉取到的那个项目就OK，不必拘泥于到底该装哪个。

23.tmux分屏功能个人觉得通过`多开putty或Xshell`替代效率更高，这条仅作为经验之谈，具体根据个人情况和喜好确定。

22.有同学问git log怎么检查，这里简单给个参考标准（**仅供参考**）：使用命令`git log --author="你在项目中设置的那个你自己的学号-姓名"`，将本次报告的进度部分中产生的手动commit的截图，然后那些make run和编译的记录有就可以，当然如果你申请了在线的代码托管，在网页上截图也可以

21.有同学反映VM按教程设置了网卡2为仅主机网络（Host-Only）后查eth1的状态出错，这个两方面可能性：一方面是你的Host-Only网卡名字不叫`eth1`，这种情况请使用`ifconfig -a`命令查看并确定哪个才是你的Host-Only网卡（一般IP分配为`10.x.x.x`的是NAT网卡，IP为`127.0.0.1`为环回网卡，不是这两个中其一的**另一个网卡**必然就是Host-Only网卡了）；另一方面可能是网卡找到了，但是没有IP，说明没启动，解决办法如下：使用命令`sudo vim /etc/network/interfaces`对网络设置文件进行修改 ，在文件末尾加入以下两行（**其中如果涉及到第一种情况，则eth1应替换为相应网卡名**）：
```
auto eth1            #自动启动eth1
iface eth1 inet dhcp #设置eth1从DHCP处获得IP
```
保存退出 ，输入命令`sudo /etc/init.d/networking restart`重启网络服务。然后最好再重启一次虚拟机确保设置成功更改。经试验发现**使用桥接模式**可实现单网卡既能上网又能让物理机连接到22端口，可以试试。

* 2018.2.26更新：

20.开学以后，你们还要兼顾很多课的进程，所以请大家**每周的PA进度一定要周中就开始做**了，留到周末做有两方面问题：一个是到后面量大了以后，`不是一两个通宵就能肝的完的`（这个光说无用，你们体会一次就知道了）；第二是集中到周末做，`问问题的人太密集太多，短时间内我也解答不过来`，等解答到你的问题的时候可能是几个小时以后了，耽误了你的进程我也很抱歉，但是没有办法；第三是`提交时间是严格截止`的，迟交了可能会被**惩♂罚**，注意一下吧

19.还没开始做的同学可以留意下，docker和vm没有绝对的哪个好哪个不好，一个是看个人习惯，一个是看自己的**OS环境能不能用docker**（只有`Windows10`**非家庭版**和`Linux当桌面`的大佬同学可以用docker）。至于用vm的同学，装机一定要装**32位（x86）的debian**，装64位理论上可做（我就是在64位CentOS上面跟着你们进度），但是需要自己安装的时候安装系列**32位的编译环境**等等（这个我自己亲自试过可行），后面可能会有未知的问题（因为我也没有在64位环境下试验过，反正去年的项目拿来是能编译能跑，今年由于代码体系不同了，谁知道会出什么问题呢），无法保证

18.报告的过程要有截图，不要等做完了突然想起来我一个图都没截，做的过程中就**一边做一边截图**，有些图可以补，但是有些就不是很好补，注意一下

* 2018.2.25更新：

17.还是发现有人不看这个问答就来问，能自助解决的问题还是请**先尝试一下问答文档里的解决方案**。

16.ping百度ping不通，可能会提示是域名解析错误，这个时候再去ping一个外网的IP地址（这里我提供我自己的服务器给大家拿去ping：IP地址为`115.159.190.100`（Linux/CentOS）和`106.14.118.136`（Windows Server）），ping IP也ping不通才是DNS解析的问题，这个搜索关键词：【`linux 域名无法解析`】

15.讲义以群文件中的【`NUAA ICS 2018.pdf`】为准，其余不管你在哪里看到的什么（包括某些人翻出来的网页版的讲义啦，哪怕是我这个问答文档也要辩证来看这些问题）都**仅供参考**

14.建议经常**备份一下虚拟机**（把整个虚拟机导出，VirtualBox和VMware都支持，这个网上查一下就明白了，很简单，就不附具体流程了，提供关键词：【`virtualbox 导出虚拟机`】【`vmware 导出虚拟机`】），docker的同学备份可能要麻烦些（因为我自己没具体操作过，这个网上也有，关键词：【`docker 导出容器`】），但是但是，最保险的是自己申请一个代码仓库（`GitHub`，`Coding`，`码云`都可以），把自己的代码push到代码仓库上面，这个的相关指导文章就数不胜数了，自己查百度即可

* 2018.2.24更新：

13.再提醒一遍，用docker做实验的同学搭SSH参考`2018讲义`，用VM的做实验的同学搭SSH参考`VM的SSH讲义`，注意`端口`不要搞混

12.关于有的同学安装了`debian的VM`，还在VM里面试图用ssh命令假装混成`GNU/Linux and Mac Users`，我只能用**请仔细理解讲义，并好好查阅这份问答文档**来回答你

11.关于SSH中你到底应该看For Windows还是For Linux/Mac Users呢？：你应该看哪个小节指的是你自己**物理机**里是啥系统，形象地说，大部分同学应该对应`For Windows Users`，**小部分平时就用Linux当桌面的大佬和用Mac OS的同学**，才参考`For GNU/Linux and Mac Users`

10.2018讲义（或VM的SSH讲义）中的ssh连接，形象地说，如果把Docker（或VM）中安装debian看作一台笔记本电脑，那么通过ssh连接（Windows下的putty/linux和mac自带的ssh功能），**就相当于给这台笔记本电脑接一个外接显示器**

9.安利部分：传文件可以用`FileZilla`提高效率，终端可以用`Xshell`替代putty（根据个人喜好）

* 2018.2.23更新：

8.重修同学，如果不想重新搭建docker环境，可以将就沿用去年的`虚拟机环境`（前提当然是你没删），但是请把去年的ics目录删掉（不删也罢，但是别搞错了哪个是哪个），2018和2017的PA用的代码框架不同（这个对比下讲义就显而易见了），因此去年不管做到哪挂的。。代码几乎没用了。。

* 2018.2.22更新：

7.开始做PA0以后**不要去瞎搞电脑**（包括重装系统，升级系统，装某某驱动，重装docker或者虚拟机什么的），这个搞坏了**只有从头做**，除非自己网上找代码仓库（比如`码云`，`github`，`coding`这些）存代码，这种情况也要重做PA0，所以这一个学期，电脑坏了只要还能将就用能做PA，就不要修电脑，期末结束了再修，否则影响了进度问题很严重

6.遇到docker好像开启了容器但是连不上，多半是上次用完没停止容器，然后挂起假死了，`stop一下，然后重启下电脑`，基本上都正常了

5.再再然后有时候遇到vim修改某某系统文件失败，麻烦用`sudo vim`来修改

4.拉取镜像慢和apt-get慢，以及拉取镜像1/11失败，apt-get失败等，解决办法都是挂VPN和换国内源（搜索关键字：【`docker 更换国内源`】【`debian 更换国内源`】【`apt-get 阿里源`】）
* docker的镜像加速（摘自菜鸟教程）：
鉴于国内网络问题，后续拉取 Docker 镜像十分缓慢，我们可以需要配置加速器来解决，我使用的是网易的镜像地址：http://hub-mirror.c.163.com。
新版的 Docker 使用 /etc/docker/daemon.json（Linux） 或者 %programdata%\docker\config\daemon.json（Windows） 来配置 Daemon。
请在该配置文件中加入（没有该文件的话，请先建一个）：
``` json
{
  "registry-mirrors": ["http://hub-mirror.c.163.com"]
}
```

3.docker命令无法识别，不是网络问题，是docker安装的有问题，解决方法是`卸载重装`，并检查`hyper-v`等是否处于正常打开状态

2.关于vmware的host-only，给一个参考博文，[请点击这里](http://blog.csdn.net/u013121305/article/details/49505679)
搜索关键词：【`linux host-only vmware`】，另外经验证使用虚拟机网卡的`桥接模式`可以连通虚拟机的22端口，可以尝试。

1.近期90%以上的问题**来自手误**，麻烦出问题的同学自己仔细**逐个字符**检查一下敲的内容（`dockerfile`，修改`debian的update源`，敲`命令`等等）有没有打错的（前几天一个比较极端的例子是`debian`打成`debain`搞了半个小时，昨天还有一个把参数的-打成全角横杠，搞了一个小时）。
* 附常见手误：
```
debian和debain
docker build -t和docker built -d
半角字符和全角字符（多半是输入法造成的）
（持续更新中...）
```
