## hi3861 代码结构
 示例代码: vendor\hisilicon\hispark_pegasus\demo\nfc_demo
 hi3861平台配置文件位于：vendor\hisilicon\hispark_pegasus\config.json
 模块:
    applications：应用子系统 applications/sample/wifi-iot/app 
    iot_hardware：硬件驱动子系统 头文件路径： base\iot_hardware\peripheral\interfaces\kits
            具体代码路径，由device\board\hisilicon\hispark_pegasus\liteos_m\config.gni文件中指定
 
 device\soc\hisilicon\hi3861v100\sdk_liteos\app\wifiiot_app\src\app_main.c

## 编译:
1. 选择目标板:
hb set -p wifiiot_hispark_pegasus
or
hb set //选择wifiiot_hispark_pegasus

2. 执行编译
hb build -f 2>&1 | tee build.log
or 
hb build -f

##
修改 device/soc/hisilicon/hi3861v100/sdk_liteos/build/config/usr_config.mk文件。在这个配置文件中打开PWM驱动宏。搜索字段CONFIG_I2C_SUPPORT ，并打开I2C

## 3816资源
OLED显示板 
NFC板                        没有驱动
智能红绿灯板 三个LED灯/光敏电  
智能炫彩灯板 RGB灯/人体红外/
环境监测板   AHT20(I2C 温湿度)  没有驱动

语音控制(讯飞API,android app)

##
1. OpenHarmony简介
2. 开发环境搭建
3. 快速入门:helloword、启动流程分析
4. OpenHarmony内核—任务管理
5. OpenHarmony内核—软件定时器
6. OpenHarmony内核—信号量
7. OpenHarmony内核—事件
8. OpenHarmony内核—互斥锁
9. OpenHarmony内核—队列
10. OpenHarmony驱动:GPIO输出-GPIO点灯
11. OpenHarmony驱动:GPIO输入-按键
12. OpenHarmony驱动:ADC
13. OpenHarmony驱动:UART
14. OpenHarmony驱动:PWM
15. OpenHarmony驱动:I2C-OLED显示驱动
16. OpenHarmony网络:WIFI连接热点
17. OpenHarmony网络通讯:UDP
18. OpenHarmony网络通讯:TCP
19. OpenHarmony物联网:MQTT
20. 智能家居实例:人体感应自动灯
21. 智能家居实例:智能门锁(NFC没有驱动)
22. 智能家居实例:智能温湿度控制器(AHT20没有驱动,MQTT)
23. 智能家居实例:语音控制的RGB彩灯(安卓App,语音识别,PWM,UDP/TCP)

##
小熊派-鸿蒙·叔(BearPi-HM Micro)
https://gitee.com/bearpi/bearpi-hm_micro_small

https://gitee.com/bearpi/bearpi-hm_nano

## 
[OpenHarmony轻量系统开发【1】初始OpenHarmony](https://harmonyos.51cto.com/posts/10085)
[OpenHarmony轻量系统开发【2】源码下载和开发环境](https://harmonyos.51cto.com/posts/10086)
[OpenHarmony轻量系统开发【3】代码编译和烧录](https://harmonyos.51cto.com/posts/10087)
[OpenHarmony轻量系统开发【4】编写第一个程序、启动流程分析](h/9ttps://harmonyos.51cto.com/posts44)
[OpenHarmony轻量系统开发【5】驱动之GPIO点灯](https://harmonyos.51cto.com/posts/1236)
[OpenHarmony轻量系统开发【6】驱动之ADC按键](https://harmonyos.51cto.com/posts/1400)
[OpenHarmony轻量系统开发【7】驱动之I2C显示OLED屏幕](https://harmonyos.51cto.com/posts/1145)
[OpenHarmony轻量系统开发【8】其它驱动开发示例](https://harmonyos.51cto.com/posts/10185)
[OpenHarmony轻量系统开发【9】WiFi之STA模式连接热点](https://harmonyos.51cto.com/posts/10191)
[OpenHarmony轻量系统开发【10】编写自己的软件包](https://harmonyos.51cto.com/posts/10192)
[OpenHarmony轻量系统开发【11】移植MQTT](https://harmonyos.51cto.com/posts/10201)
[OpenHarmony轻量系统开发【12】OneNET云接入](https://harmonyos.51cto.com/posts/10204)
[OpenHarmony轻量系统开发【13】鸿蒙小车开发](https://harmonyos.51cto.com/posts/1459)
[OpenHarmony轻量系统开发【14】使用语音控制鸿蒙小车](https://harmonyos.51cto.com/posts/1842)




git push -u origin main