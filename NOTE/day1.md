# 进入main函数后
## （1）内存划分
- 设置边界值：
    - 内核程序
    - 缓冲区：加速磁盘的读写效率
    - 主内存：
## （2）mem_init函数
- 对主内存区域用mem_map[]进行管理
- 通过buffer_init函数，对缓冲区区域（双向链表缓冲头 和 缓冲块）进行管理，再用一个hashmap索引所有缓冲头
## （3）trap_init函数
- 设置中断描述符表的一些默认中断
## （4）blk_dev_init
- 对读写块设备的管理进行初始化，
## （5）tty_init 控制台初始化
- 通过tty_init里的con_init,实现控制台输出字符的功能
## （6）sched_init 进程调度初始化
- 初始化函数 shed_init，定义好了全部进程的管理结构 task[64] 数组，并在索引 0 位置处赋上了初始值，作为零号进程的结构体
## （7）hd_init 硬盘初始化
开启硬盘中断处理函数，可以通过硬盘的端口与其进行读写交互