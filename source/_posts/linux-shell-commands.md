title: linux shell commands
date: 2015-09-08 17:29:51
tags:
- LINUX
- cmd-line
---

> #实用性linux命令

***

##shell cmd
 ###1. top
 ###2. ps

***
###1. top
![topCmd](/imgs/linux-shell-commands/topCMD.jpg)
1. top - 17:26:23 up 19 days, 3:47 1 user, load average: 0.09, 0.25, 0.24
  * 17:26:23, 当前时间
  * up 19 days, 3:47,系统运行时间,19天,3小时47分钟
  * 1 user, 当前登录用户数
  * load average: 0.09,0.25,0.24,系统负载,任务队列的平均长度。3个值分别为,1分钟,5分钟,15分钟前到现在的平均值.

2. Tasks: 82 total, 1 running, 81 sleeping, 0 stopped, 0 zombie
  * Tasks: 进程相关数据
  * 82 total 进程总数
  * 1 running, 正在运行的进程数
  * 81 sleeping, 睡眠的进程数
  * 0 stopped, 停止的进程数
  * 0 zombie, 僵尸进程数

3. Cpu(s): 0.2%us, 0.2%sy, 0.0%ni, 99.7%id, 0.0%wa, 0..0%hi, 0.0%si, 0.0%stopped
  * Cpu(s): cpu相关数据,cpu占用百分比
  * 0.2%us, 用户空间占用cpu百分比
  * 0.2%sy, 内核空间占用cpu百分比
  * 0.0%ni, 用户进程空间内改变过优先级的进程占用cpu百分比
  * 99.7%id, 空闲cpu百分比
  * 0.0%wa, 等待输入输出的cpu时间百分比
  * 0.0%hi, 硬件中断占用cpu百分比
  * 0.0%si, 软件中断占用cpu百分比
  * 0.0%st, 盗取时间(超级监视器服务其他cpu时,虚拟cpu等待的时间)
  
4. Mem: 3921112k total, 3670576k userd, 250536k free, 142524k buffers
  * Mem: 物理内存使用量
  * 3921112k total : 物理内存总量
  * 3670576k used: 使用量
  * 250536k free: 空闲内存总量
  * 142524k buffers: 用作内核缓存的内存量
  
5. Swap: ok total, ok used, ok free, 1401036k cached
  * Swap: 交换区
  * 0k total: 使用的交换区总量
  * 0k used: 空闲的交换区总量
  * 1401036k cached: 缓冲的交换区总量。 内存中的内容被换出到交换区，而后又被换入到内存，
    但使用过的交换区尚未被覆盖，该数值即为这些内容已存在于内存中的交换区的大小。
    相应的内存再次被换出时可不必再对交换区写入。
    
6. 其他
  * PID :进程id
  * PPID :父进程id
  * RUSER :real user name
  * UID: 进程所有者的用户id
  * USER: 进程所有者的用户名
  * GROUP: 进程所有者的组名
  * TTY: 启动进程的终端名。
  * PR: 优先级
  * NI: nice值,负值表示表示高优先级。
  * P: 最后使用的CPU,仅在多cpu环境下有意义
  * %CPU: 上次更新到现在的cup时间占用百分比
  * TIME: 进程使用的CPU时间总计,单位秒
  * TIME+: 进程使用的cpu时间总计,单位1/100秒
  * %MEM: 进程使用的物理内存百分比
  * VIRT: 进程使用的虚拟内存总量,单位kb.VIRT=Swap+RES
  * SWAP: 进程实用的虚拟内存中,被换出的大小,单位kb
  * RES: 进程使用的,为被换出的物理内存大小,单位kb,RES=CODE+DATA
  * CODE: 可执行代码占用的内存大小,单位kb
  * DATA: 可执行代码以外的部分(数据段+栈)占用的物理内存大小,单位kb
  * SHR：共享内存大小,单位kb
  * nFLT: 页面错误次数
  * nDRT: 最后一次写入到现在,被修改过的页面数
  * 进程状态:
    S=睡眠,D=不可中断的睡眠状态,R=运行,T=跟踪/停止,Z=僵尸进程
  * COMMAND: 命令名
  * WCHAN: 若该进程在睡眠,则显示睡眠中的系统函数名
  * Flags: 任务标志.
  
  
### 2. ps
* ps -aux | grep redis | grep -v grep 
  显示进程名称包含redis的进程,显示进程名称不包含grep的进程。