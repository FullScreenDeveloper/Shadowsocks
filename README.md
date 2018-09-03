# Shadowsocks
How to build your own Shadowsocks

// TOD 未完成

## 什么是VPS
[百度百科-VPS](https://baike.baidu.com/item/VPS)
## 购买bandwagonhost的VPS
搬瓦工，因其官网网站标识是BandwagonHost，有点类似BanWaGong的拼写，所以我们国内的站长喜欢称作为搬瓦工VPS。以下是两个重要的网站:
- [搬瓦工官网](https://bwh1.net/)
- [搬瓦工中文网-非官方](http://banwagong.cn/)

如何选购VPS配置？
当前选择购买VPS的主要目的是搭建Shadowsocks，所以选择最低配置(*最便宜)*的就够用了，最重要的是能够直接使用支付宝付款啊，也就是下面这款：

![版完工套餐](http://obh9jd33g.bkt.clouddn.com/writestory/1534082013378.jpg)

一年19.99美刀，将近130人民币，算上来是十分的划算了，加上优惠码的话还能打将近6%的折扣。

[19.99购买地址](https://bwh1.net/cart.php?a=confproduct&i=0)

加入购物车：

![购买页面](http://obh9jd33g.bkt.clouddn.com/writestory/1534082147767.jpg)

输入优惠码

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

安装新的系统，这里我们选择Centos 7 x86_64即可。注意的是安装成功会返回一个端口号和登陆密码，需要将这两个东西保存好，以便后续的操作。

![选择系统](http://obh9jd33g.bkt.clouddn.com/writestory/1534083004026.jpg)

![密码和端口号](http://obh9jd33g.bkt.clouddn.com/writestory/1534083161983.jpg)

# 安装Shadowsocks
虽然搬瓦工提供了一键安装方式，但并不建议直接使用，而是建议自行安装，这样也能了解流程和配置多账号也比较方便。

![一键安装Shadowsocks](http://obh9jd33g.bkt.clouddn.com/writestory/1534083280313.jpg)

准备相关工具
mac
windows 