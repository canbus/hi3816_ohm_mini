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
3. helloword、启动流程分析
4. GPIO输出驱动:GPIO点灯
5. GPIO输入驱动:按键
6. GPIO驱动:ADC
7. PWM控制:
8. I2C驱动:OLED显示驱动
9. WIFI连接热点
10. 网络通讯:UDP
11. 网络通讯:TCP
12. IOT:MQTT
13. 智能家居实例:人体感应自动灯
14. 智能家居实例:智能门锁(NFC没有驱动)
15. 智能家居实例:智能温湿度控制器(AHT20没有驱动,MQTT)
16. 智能家居实例:语音控制的RGB彩灯(安卓App,语音识别,PWM,UDP/TCP)

##
小熊派-鸿蒙·叔(BearPi-HM Micro)
https://gitee.com/bearpi/bearpi-hm_micro_small

## 
[OpenHarmony轻量系统开发【1】初始OpenHarmony](https://harmonyos.51cto.com/posts/10085)
[OpenHarmony轻量系统开发【2】源码下载和开发环境](https://harmonyos.51cto.com/posts/10086)
[OpenHarmony轻量系统开发【3】代码编译和烧录](https://harmonyos.51cto.com/posts/10087)
[OpenHarmony轻量系统开发【4】编写第一个程序、启动流程分析](https://harmonyos.51cto.com/posts/944)
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



echo "# hi3816_ohm_mini" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/canbus/hi3816_ohm_mini.git
git push -u origin main