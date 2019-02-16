
## adb 常用的输出语句

1.adb devices   
第一次输入显示出：  
    C:\Users\Administrator>adb devices
    List of devices attached
    * daemon not running. starting it now at tcp:5037 *
    * daemon started successfully *
表示服务启动成功，当前没有连接Android手机，所以后面没有出现设备名称  

2.adb logcat
adb logcat > 地址     可以将日志输出到电脑中的文件上面
