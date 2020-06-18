# BenOS 中文名： 笨OS

笨OS是笨叔的OS，为《Arm64体系结构编程与实践》一书操作系统大综合实验，大家可以当做练手的一个项目，把闲置的树莓派玩起来。

《Arm64体系结构编程与实践》一书已经在2022年4月出版。
购买：        
JD： https://item.jd.com/13119117.html           
当当： http://product.dangdang.com/29384351.html     

本书资料下载： 关注"奔跑吧linux社区“微信公众号，输入”arm64“获取。


## BenOS的来由
学习操作系统最有效及最具有挑战性的训练是从零开始动手写一个小操作系统（OS）。目前很多国内外知名大学的操作系统课程的实验都与动手写一个小OS相关，比如麻省理工大学的操作系统课程采用xv6系统来做实验。xv6是在x86处理器上重新实现的Unix第六版系统，用于教学目的。清华大学的操作系统课程也采用类似的思路，他们基于xv6的设计思想，通过实验一步一步完善一个小操作系统：ucore OS。xv6和ucore OS实验都是采用类似英语考试中完成填空式的方式来引导大家实现和完善一个小OS。

动手写一个小操作系统会让我们对计算机底层技术有更深的理解，对操作系统中核心功能，比如系统启动、内存管理、进程管理等内容理解也会有更深刻。我们设计了20多个小实验引导读者在树莓派上从零开始实现一个小操作系统，我们把这个小操作系统命名为：BenOS。
## 实验设备：
1. 硬件开发平台：树莓派4B
2. 软件模拟平台：QEMU 4.2
3. 处理器架构：ARMv8架构（aarch64）
4. 开发主机：Ubuntu Linux 20.04
5. MicroSD卡一张以及读卡器
6. USB转串口线一根
7. ARM硬件仿真器，例如JLINK仿真器（可选）

## 芯片资料
本章使用到的芯片手册如下。
1. 《ARM Architecture Reference Manual, ARMv8, for ARMv8-A architecture profile》，v8.6版本。
2. 《BCM2837 ARM Peripherals》，v2.1版本，用于树莓派3B。
3. BCM2711芯片手册：《BCM2711 ARM Peripherals》，v1版本，用于树莓派4B。

## 实验安排
本章实验按照难易程度分成三个阶段。
1. 入门动手篇。对于一般读者完成相对容易的5个小实验之后，对ARM64体系结构、操作系统启动、中断和进程管理会有初步的认识。
2. 进阶挑战篇。对操作系统有浓厚兴趣以及学有余力的读者可以完成进阶篇的12个实验。这12个实验包括了操作系统最核心的功能，比如物理内存管理、虚拟内存管理、缺页异常处理、进程管理以及进程调度等。
3. 高手完善篇。对操作系统有执着追求的读者可以继续完成高手篇的实验，这样一步一步实现了一个有一定使用价值的小操作系统。
本章所有实验为开放性实验，读者可以根据实际情况来选做部分或者全部实验。

## 实验目录

#### 入门动手篇
1. 实验1：打印“Welcome，BenOS”        （Done）
2. 实验2：切换异常等级                （Done）
3. 实验3：实现简易的printk打印函数     （Done）
4. 实验4：中断实验                    （Done）
5. 实验5：进程创建实验                （Done）
#### 进阶挑战篇
6. 实验6：进程调度实验                 （Done）
7. 实验7：中断注册                     （Done）
8. 实验8：让进程运行在用户态
9. 实验9：添加系统调用
10. 实验10：实现一个简单的物理内存页面分配器
11. 实验11：实现一个简单的小块内存分配器
12. 实验12：建立恒等映射页表
13. 实验13：实现简单的虚拟内存管理
14. 实验14：实现缺页异常机制
15. 实验15：实现panic功能和打印函数调用栈
16. 实验16：实现用户空间的内存分配函数
17. 实验17：写时复制功能的实现
18. 实验18：进程生命周期管理
#### 高手完善篇
19. 实验19：信号量
20. 实验20：软中断机制
21. 实验21：编写SD卡的驱动
22. 实验22：设计和实现虚拟文件系统层
23. 实验23：实现ext2文件系统
24. 实验24：实现execv系统调用
25. 实验25：实现简单的shell界面
26. 实验26：添加多核SMP的支持

## 邀请一起玩BenOS
邀请小伙伴参与BenOS开发.

开发要求：
1. 代码设计合理，注释合理。
2. 设计合理的实验测试用例。
3. 代码格式要求，符合linux内核代码规范，必须要通过linux内核checkpatch.pl脚本的格式检查。
4. patch分割合理，每个小功能一个小patch。
5. 必须在QEMU和树莓派上都能运行，包括树莓派3B和树莓派4B

## 代码checkin要求

所有代码patch都必须经过checkpatch.pl脚本的检查。
```
$ git diff | ./scripts/checkpatch.pl --no-tree

对于新创建文件：
$ git add new_file
$ git diff --cached | ./scripts/checkpatch.pl --no-tree
```
除了printk函数的警告以及文件版权警告不用fix，其他的都需要fix。

## 代码组织
每个小实验一个分支，例如lab01，可以git checkout lab01分支。
每个实验都可以单独维护。

armv8_dev是主开发分支。

master是用来存放文档和芯片手册。

## 奔跑吧视频课程
有兴趣的读者可以订阅奔跑吧旗舰篇视频课程，目前有两季
1. 第一季，内存管理专题
2. 第二季，进程管理，锁，中断三合一
3. 死机黑屏专题，介绍kdump+crash如何解决死机难题。
4. 第3季 Arm64体系结构编程与实践

奔跑吧视频课程，基于Linux 5.0进行讲解，手把手分析Linux 5.0内核源代码。
我们是按照专题来收费，比如您订阅了第一季，以后录制和内存管理相关的视频，都统统免费。

订阅地址：https://shop115683645.taobao.com/
