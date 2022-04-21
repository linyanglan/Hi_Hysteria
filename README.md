# Hi Hysteria

## 一·简介
> Hysteria 是一个功能丰富的，专为恶劣网络环境进行优化的网络工具（双边加速），比如卫星网络、拥挤的公共 Wi-Fi、在**中国连接国外服务器**等。 基于修改版的 QUIC 协议。

Hysteria这是一款由go编写的非常优秀的“轻量”代理程序，它很好的解决了在搭建富强魔法服务器时最大的痛点——**线路拉跨**。

在魔法咏唱时最难的不是搭建维护，而是在晚高峰时期的交付质量。~~当三大运营商晚高变成了：奠信、连不通、移不动时，你我都有感触。~~ 虽然是走的udp但是提供obfs，暂时不会被运营商针对性的QoS(不开obfs也不会被QoS)。

1、原项目提供的bench:

![image](https://raw.githubusercontent.com/HyNetwork/hysteria/master/docs/bench/bench.png)

2、50mbps北方电信,北京出口 直连落地vir San Jose机房163线路，22-23点测试YT 1080p60直播流:

![image](https://cloud.iacg.cf/0:/normal/img/hihysteria/speed.png)

```
190 dropped of 131329
```

3、无对钟国大陆线路优化，洛杉矶shockhosting机房，1c128m ovznat 4k@p60：
![image](https://raw.githubusercontent.com/emptysuns/Hi_Hysteria/main/imgs/yt.jpg)
```
139783 Kbps
```
该项目仅作学习用途，请查看的访客在5s之内立即删除并停止使用。

由它所引起的任何问题，作者并不承担风险和任何法律责任。

因为脚本现处于0.x的测试版本，可能会有一些bug，如果遇到请发issue，欢迎star，您的⭐是我维护的动力。

适配ubuntu/debian, centos/rhel操作系统,misple/arm/x86/s390x架构。

windows使用请仔细阅读[cmd客户端(伪)介绍](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/cmd.md)其他平台看[这里](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/others.md)。


```
(2022/04/18) 0.3.5:
1. 完善开放防火墙端口的流程,为以后进一步细分端口打基础
2. 加入s390x架构适配
3. 加入v2rayN的说明[TEST]
```
[历史改进](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/log.md)

## 二·使用
### 第一次使用?

#### 1. [防火墙问题](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/firewall.md)

#### 2. [自签证书](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/certificate.md)


#### 3. [限制UDP的服务商排雷列表【2022/03/21更新】](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/blacklist.md)

#### 4. [hysteria各个协议介绍](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/protocol.md)

#### 5. [cmd客户端(伪)介绍](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/cmd.md)

#### 6. [部分其他平台？](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/others.md)

#### 7. [如何设置我的延迟、上行/下行速度？](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/speed.md)

#### 8. [图形UI,v2rayN](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/v2n.md)


### 拉取安装

```
su - root #Change to root
bash <(curl -fsSL https://git.io/hysteria.sh)
```

### 配置过程
首次安装后: `hihy`命令调出菜单,如更新了hihy脚本，请执行选项`9`或者`12`,获得最新的配置
```
 -------------------------------------------
|**********      Hi Hysteria       **********|
|**********    Author: emptysuns ************|
|**********     Version: 0.3.5     **********|
 -------------------------------------------
Tips:hihy 命令再次运行本脚本.
............................................. 
############################### 

..................... 
1)  安装 hysteria 
2)  卸载 hysteria 
..................... 
3)  启动 hysteria 
4)  暂停 hysteria 
5)  重新启动 hysteria 
6)  运行状态 
..................... 
7)  更新hysteria core 
8)  查看当前配置 
9)  重新配置hysteria 
10) 切换ipv4/ipv6优先级 
11) 更新hihy 
12) 完全重置所有配置 

############################### 


0)退出 
............................................. 
请选择:
```
**脚本每次更新都可能会发生改变，请一定要展开并仔细参考演示过程，避免发生不必要的错误！**
<details>
  <summary>演示较长，点我查看</summary>
    <pre><blockcode> 
请选择:1
Ready to install.

Update.wait...
Get:1 <http://security.ubuntu.com/ubuntu> bionic-security InRelease [88.7 kB]
Hit:2 <http://archive.ubuntu.com/ubuntu> bionic InRelease
Get:4 <http://archive.ubuntu.com/ubuntu> bionic-updates InRelease [88.7 kB]
Hit:3 <https://packagecloud.io/ookla/speedtest-cli/ubuntu> bionic InRelease
Get:5 <http://archive.ubuntu.com/ubuntu> bionic-backports InRelease [74.6 kB]
Fetched 252 kB in 2s (118 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
72 packages can be upgraded. Run 'apt list --upgradable' to see them.

Done.
Install wget curl netfilter-persistent lsof
*wget
Installed.Ignore.
*curl
Installed.Ignore.
*netfilter-persistent
Installed.Ignore.
*lsof
Installed.Ignore.

Done.
The Latest hysteria version:v1.0.3
Download...

Download completed.
开始配置:
请输入您的域名(不输入回车,则默认自签wechat.com证书,不推荐):

您选择自签wechat证书.公网ip:1.2.3.4

请输入你想要开启的端口,此端口是server端口,建议10000-65535.(默认随机)

随机端口:10294

选择协议类型:

1、udp(QUIC)
2、faketcp
3、wechat-video(回车默认)

输入序号:
2
IPTABLES OPEN: tcp/10294
传输协议:faketcp

请输入您到此服务器的平均延迟,关系到转发速度(默认200,单位:ms):
60

期望速度,这是客户端的峰值速度,服务端默认不受限。Tips:脚本会自动*1.25做冗余，您期望过低或者过高会影响转发效率,请如实填写!
请输入客户端期望的下行速度:(默认50,单位:mbps):
200
请输入客户端期望的上行速度(默认10,单位:mbps):
40
请输入认证口令:
pekopeko

配置录入完成!

执行配置...
SIGN...
.
.
.
Signature ok
subject=C = CN, ST = GuangDong, L = ShenZhen, O = PonyMa, OU = Tecent, emailAddress = admin@qq.com, CN = Tencent Root CA
Getting CA Private Key
SUCCESS.

Wait,test config...

Test success.
net.core.rmem_max = 8000000
install.sh: line 533: 27680 Killed                  /etc/hihy/bin/appS -c /etc/hihy/conf/hihyServer.json server > /tmp/hihy_debug.info 2>&1
Created symlink /etc/systemd/system/multi-user.target.wants/hihy.service → /etc/systemd/system/hihy.service.
配置文件输出如下且已经在本目录生成(直接下载本目录生成的config.json[推荐]/自行复制粘贴到本地)

Tips:客户端默认只开启http(8888)、socks5(8889)代理!其他方式请参照hysteria文档自行修改客户端config.json
***********************************↓↓↓copy↓↓↓*******************************↓
{
"server": "1.2.3.4:10294",
"protocol": "faketcp",
"up_mbps": 50,
"down_mbps": 250,
"http": {
"listen": "127.0.0.1:8888",
"timeout" : 300,
"disable_udp": false
},
"socks5": {
"listen": "127.0.0.1:8889",
"timeout": 300,
"disable_udp": false
},
"alpn": "h3",
"acl": "acl/routes.acl",
"mmdb": "acl/Country.mmdb",
"auth_str": "pekopeko",
"server_name": "wechat.com",
"insecure": true,
"recv_window_conn": 7864320,
"recv_window": 31457280,
"disable_mtu_discovery": true,
"resolver": "119.29.29.29:53",
"retry": 3,
"retry_interval": 3
}
↑***********************************↑↑↑copy↑↑↑*******************************↑

Shadowrocket/Sagernet/Passwall一键链接:
hysteria://1.2.3.4:10294?protocol=faketcp&auth=pekopeko&peer=wechat.com&insecure=1&upmbps=50&downmbps=250&alpn=h3#Hys-1.2.3.4

安装完毕
root@ubuntu:~/hysteria# systemctl status hihy
● hihy.service - hysteria:Hello World!
   Loaded: loaded (/etc/systemd/system/hihy.service; enabled; vendor preset: enabled)
   Active: active (running) since Mon 2022-04-18 01:45:35 EDT; 25s ago
 Main PID: 27793 (appS)
    Tasks: 6 (limit: 1077)
   CGroup: /system.slice/hihy.service
           └─27793 /etc/hihy/bin/appS --log-level warn -c /etc/hihy/conf/hihyServer.json server

Apr 18 01:45:35 ubuntu systemd[1]: Started hysteria:Hello World!.

  </blockcode></pre>
</details>


## 三·高级玩法(伪

#### 1. [借用其他支持Socks5的GUI，来获得一个图形界面](https://github.com/emptysuns/Hi_Hysteria/blob/main/md/gui.md)


## 四·Todo

**如果您有好的功能建议，请不要忘记开个issue提出来欧～～～欢迎PR来完成Todo或者给我纠正我的渣代码**

**我的爱好是写bug （￣▽￣）~**

* [x] 检测端口是否被占用
* [ ] 利用xray s5 inbound来支持按域名分流(warp)
* [x] 生成分享链接
* [ ] 客户端自动更新
* [x] hihy替换掉hysteria
* [ ] 规范化脚本代码
* [ ] 利用docker安装?(不知道是否有必要)
* [ ] 多密码支持
* [ ] 利用base64加密替换原来的auth_str
* [ ] 兼容v2rayN,放弃cmd的更新

## 五·结语

魔改UDP的QUIC协议，加了tls和混淆的话，个人跑了一段时间大流量，未被运营商QoS，落地ip并没有被墙，也不知道什么时候被针对，大家且用且珍惜吧。


## 六·鸣谢


[@HyNetwork/hysteria](https://github.com/HyNetwork/hysteria)


[@Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip)


[@mack-a/v2ray-agent](https://github.com/mack-a/v2ray-agent)
