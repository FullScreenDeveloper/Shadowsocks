
# update
> 2018年9月29日
> 1. 更新截图
> 2. 更新加密模式


# 如何搭建自己的Shadowsocks


主要有以下步骤：
> 1. 购买境外VPS
> 2. VPS中安装Shadowsocks
> 3. VPS中启动Shadowsocks服务
> 4. 使用客户端Shadowsocks


# 什么是VPS
[百度百科-VPS](https://baike.baidu.com/item/VPS)
# 购买bandwagonhost的VPS
搬瓦工，因其官网网站标识是BandwagonHost，有点类似BanWaGong的拼写，所以我们国内的站长喜欢称作为搬瓦工VPS。

如何选购VPS配置？

当前选择购买VPS的主要目的是搭建Shadowsocks，所以选择最低配置(*最便宜)*的就够用了，最重要的是能够直接使用支付宝付款啊，也就是下面这款：

![19.9美元套餐](http://obh9jd33g.bkt.clouddn.com/writestory/1537965460533.png)

一年19.99美刀，将近130人民币，算上来是十分的划算了，加上优惠码的话还能打将近6%的折扣。

[19.99购买地址](https://bwh1.net/index.php?aff=37047)

加入购物车：

![购买页面](http://obh9jd33g.bkt.clouddn.com/writestory/1534082147767.jpg)

输入优惠码
[优惠码领取](https://www.bandwagonhost.net/coupon)

![输入优惠码](http://obh9jd33g.bkt.clouddn.com/writestory/1534082287860.jpg)


折扣了1.25美刀

![折扣1.25美刀](http://obh9jd33g.bkt.clouddn.com/writestory/1534082362160.jpg)

生成订单

![生成订单1](http://obh9jd33g.bkt.clouddn.com/writestory/1534082428750.jpg)

填写相关信息，注意这一步相当于创建一个搬瓦工账号，而且在验证信息的时候是不能挂VPN的

![填写订单信息](http://obh9jd33g.bkt.clouddn.com/writestory/1534082508032.jpg)

选择付款方式，选择支付宝付款方式

![选择付款方式](http://obh9jd33g.bkt.clouddn.com/writestory/1534082632301.jpg)

付款

![付款](http://obh9jd33g.bkt.clouddn.com/writestory/1534082655614.jpg)

付款成功后我们的搬瓦工后台就有一台vps服务器了

![搬瓦工vps服务器列表](http://obh9jd33g.bkt.clouddn.com/writestory/1534082768345.jpg)

点击**KiwiVM Control Panel**打开管理控制面板

![管理面板](http://obh9jd33g.bkt.clouddn.com/writestory/1534082931146.jpg)

安装新的系统（安装之前需要先停止VPS），这里我们选择Centos 7 x86_64即可。注意的是安装成功会返回一个端口号和登陆密码，需要将这两个东西保存好，以便后续的操作。

![选择系统](http://obh9jd33g.bkt.clouddn.com/writestory/1534083004026.jpg)

![密码和端口号](http://obh9jd33g.bkt.clouddn.com/writestory/1538216321625.png)

# 安装Shadowsocks
虽然搬瓦工提供了一键安装方式，但并不建议直接使用，而是建议自行安装，这样也能了解流程和配置多账号也比较方便。

![一键安装Shadowsocks](http://obh9jd33g.bkt.clouddn.com/writestory/1534083280313.jpg)

## 登录VPS
本次演示使用的是windows系统，登录工具为：PuTTY，登录用户为root，
使用root用户登录，进入到Linux控制台，首先对可用软件源进行升级
> yum update

这里我们使用Python版的Shadowsocks，方便日后的管理。先安装Python环境以及pip
> yum install python-setuptools
>  easy_install pip

PS:要升级的话不要做以上操作成功后，安装Shadowsocks
> pip install shadowsocks

至此，Shadowsocks安装完毕。

## 配置Shadowsocks

在当前root用户的个人文件夹下新建一个Shadowsocks的配置文件
> vi /root/shadowsocks.json

这里以创建多个账号为例
```json
{
	"server": "你的IP地址",
	"local_address": "127.0.0.1",
	"port_password": {
		"8381": "自定义一个该端口的密码",
		"8382": "自定义一个该端口的密码"
	},
	"timeout": 300,
	"method": "aes-256-cfb",
	"fast_open": false,
	"workers": 1
}
```
|参数名|    说明|
|---------|-----------|
|server   |当前服务器IP|
|port_password   |要建立的端口号和密码（可以定义多个端口和密码供多设备使用）|
|timeout   |超时时间（秒）|
|method  |加密方法（推荐使用aes-256-cfb）|
fast_open  |如果VPS的Linux内核在3.7以上，可以设置为true开启，以降低延迟|
|workers    |works数量，默认为1|

编辑好后保存并退出。
> 按下 esc
> 输入  *:wq*
> 回车

启动
> ssserver -c /root/shadowsocks.json

这里启动是直接在当前命令行中启动的，一旦关闭窗口就会关闭服务(Web端除外)，需要加上**nohup**

> nohup ssserver -c /root/shadowsocks.json

![启动成功](http://obh9jd33g.bkt.clouddn.com/writestory/1538217009159.png)

 自启动
>echo "ssserver -c /root/shadowsocks.json -d start" >> /etc/rc.d/rc.local



如上图，启动成功，关闭连接即可。

# 使用Shadowsocks
下载Shadowsocks客户端，这里需要说明的是：请勿在其它第三方网站下载Shadowsocks，防止被人加料，可以直接渠道[Shadowsocks的GitHub](https://github.com/shadowsocks)上面进行下载，提供了windows、Android、MAC等平台的安装包。

## 配置Shadowsocks
右键小飞机，编辑服务器

![编辑服务器1](http://obh9jd33g.bkt.clouddn.com/writestory/1537964867254.png)

输入相关信息

![输入服务器信息](http://obh9jd33g.bkt.clouddn.com/writestory/1538218802382.png)

输入完成点击确定，右键小飞机。

![启动服务](http://obh9jd33g.bkt.clouddn.com/writestory/1537965093460.png)

> PAC模式是指需要的情况下再使用Shadowsocks
> 全局模式，每个网络请求都走代理

启动完成可以输入google.com查看成果

![google](http://obh9jd33g.bkt.clouddn.com/writestory/1537965177364.png)


# 最后
未完待续，持续更新。
