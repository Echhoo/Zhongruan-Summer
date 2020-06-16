# Linux命令
> [菜鸟教程](https://www.runoob.com/linux/linux-command-manual.html) \
> [csdn](https://blog.csdn.net/qq_41923771/article/details/81452529)

## 关于关机
shutdown 会给系统计划一个时间关机。它可以被用于停止、关机、重启机器。shutdown 会给系统计划一个时间关机。它可以被用于停止、关机、重启机器。
```
# shutdown -p now  // 关闭机器
# shutdown -H now  // 停止机器      
# shutdown -r09:35 // 在 09:35am 重启机器
```
要取消即将进行的关机，只要输入下面的命令：
```
# shutdown -c
```
halt 命令通知硬件来停止所有的 CPU 功能，但是仍然保持通电。你可以用它使系统处于低层维护状态。注意在有些情况会它会完全关闭系统。
```
# halt             // 停止机器
# halt -p          // 关闭机器、关闭电源
# halt --reboot    // 重启机器
```
poweroff 会发送一个 ACPI 信号来通知系统关机。
```
# poweroff           // 关闭机器、关闭电源
# poweroff --halt    // 停止机器
# poweroff --reboot  // 重启机器
```
reboot 命令 reboot 通知系统重启。
```
# reboot           // 重启机器
# reboot --halt    // 停止机器
# reboot -p        // 关闭机器
```

