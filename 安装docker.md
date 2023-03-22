Hi3861 Docker编译环境

# 说明
docker编译环境对外的ssh服务：
地址: 使用主机ip地址
端口：52222，端口可以自定义
系统账户：root
默认密码：123456
docker编译环境中，代码目录为/home/openharmony_mini
docker编译环境操作系统为Ubuntu20.4，Python 3.8.10



# 安装docker
使用官方安装脚本自动安装docker
`curl -sSL https://get.daocloud.io/docker | sh`

下载镜像:链接: https://pan.baidu.com/s/1LCOuu-wfb7wCYyS1czn19w 提取码: pt3i

解压: 解压后文件：embedded-race-hisilicon-track-2022_mini_v0.2.0.tar

导入：`docker load < embedded-race-hisilicon-track-2022_mini_v0.2.0.tar`

查看：`docker image ls`

启动docker编译环境
启动新的docker编译环境：
### 方式一：使用host网络，推荐使用，可配合DevEco Tool使用
`docker run -it --name openharmony_mini --net=host embedded-race-hisilicon-track-2022_mini:0.2.0`

### 方式二：使用端口映射
`docker run -it --name openharmony_mini -p 52222:52222  embedded-race-hisilicon-track-2022_mini:0.2.0`

### 启动后，出现类似如下信息，说明启动正常
```bash
# * Restarting OpenBSD Secure Shell server sshd        [ OK ]
# root@bae85ba0f77c:/home/openharmony_mini#
```
如果需要修改对外的ssh端口，请启动时，将上述指令中的52222修改为实际需要的

# 编译代码
 以下操作，在在docker编译环境中进行，且当前目录需为/home/openharmony_mini
```bash
## 切换到代码目录
cd /home/openharmony_mini

# 方式一：直接设置开发板为wifiiot_hispark_pegasus
hb set -p wifiiot_hispark_pegasus

# 方式二：执行如下指令后选择wifiiot_hispark_pegasus，再回车选定
hb set

# 执行编译
hb build -f 2>&1 | tee build.log

# 编译结束后，出现如下信息表示成功：
# [OHOS INFO]
# [OHOS INFO] wifiiot_hispark_pegasus build success
# [OHOS INFO] cost time: 0:01:05
```

## 编译失败怎么办？
请向上滚动编译窗口，查看错误信息；
或者执行命令 less build.log ，查看错误信息

## 使用ssh连接
在主机或者其他电脑上，执行如下指令进项连接，默认密码为123456
```bash
# 方式一：使用host网络，请首先在docker环境内执行ifconfig docker0获取ip地址
ssh root@docker0的ip -p 52222

# 方式二：使用端口映射
ssh root@docker编译环境主机ip -p 52222

# 在一台电脑上，首次连接时，会提示如下信息，输入yes回车即可
# Are you sure you want to continue connecting (yes/no/[fingerprint])?yes

# 根据提示root@192.168.1.15's password:输入密码回车后，显示如下信息表示登陆成功：
# Welcome to Ubuntu 20.04.3 LTS (GNU/Linux 5.10.104-linuxkit x86_64)
#
# * Documentation:  https://help.ubuntu.com
# * Management:     https://landscape.canonical.com
# * Support:        https://ubuntu.com/advantage
#
# This system has been minimized by removing packages and content that are
# not required on a system that users do not log into.
#
# To restore this content, you can run the 'unminimize' command.
# Last login: Sun May  1 10:02:02 2022 from 172.17.0.1
# root@bae85ba0f77c:/home/openharmony_mini#
```

## 文件拷贝
主机拷贝文件到docker编译环境里：

在主机上，执行如下指令
`docker cp 源文件 openharmony_mini:/目标文件`
源文件：主机上的，可为文件或者目录

目标文件：docker编译环境里的，通常为目录，表示将文件拷贝到该目录下

### docker编译环境拷贝文件到主机：

在主机上，执行如下指令
`docker cp openharmony_mini:/源文件 目标文件`

如拷贝编译后的镜像文件目录
`docker cp openharmony_mini:/home/openharmony_mini/out/hispark_pegasus/wifiiot_hispark_pegasus ./ `
源文件：docker编译环境里的，可为文件或者目录
目标文件：主机上的，通常为目录，表示将文件拷贝到该目录下

## 再次启动docker编译环境
如果退出上述docker编译环境，需要再次启动dcoker编译环境进入：
```bash
# 查看当前运行的docker实例状态
docker ps -a

# 在上一条指显示结果列表中，查看openharmony_mini的STATUS
# 如为 Exited，则需要执行下面这条指令，再次启动
# 如为 Up，则跳过下面这条指令
docker start openharmony_mini

# 进入docker编译环境
docker exec -it openharmony_mini bash
# 执行后，出现类似如下信息，说明再次进入成功
# root@bae85ba0f77c:/home/openharmony_mini#
```

## 删除docker编译环境【谨慎操作，不可恢复】
```bash
# 查看当前运行的docker实例状态
docker ps -a

# 在上一条指显示结果列表中，查看openharmony_mini的STATUS
# 如为 Up，则需要执行下面这条指令，停止其运行
# 如为 Exited，则跳过下面这条指令
docker stop openharmony_mini

# 删除
docker rm openharmony_mini
```