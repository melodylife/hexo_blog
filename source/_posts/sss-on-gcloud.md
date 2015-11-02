title: "使用GoogleCloud VPS搭建 Shadowsocks"
date: 2015-10-24 03:07:22
tags:
---


很多同学可能一直在位如何科学上网而烦恼。这确实是一个头疼的问题。当然，科学上网有很多种方法，我尝试过的如下

1. 修改Host
2. 修改DNS
3. VPN
4. Shadowsocks

当然，方法不仅限于这几种。很多牛人估计见到我这些也会不屑表示这是小儿科而已。
不过就算是小儿科，自己用的爽就好。我们家的情况是，一台小米mini，刷了潘多拉，搭建了一个Shadowsocks穿透防火墙。SS的服务器，我最初尝试过DigitalOcean新加坡，以及Vultr日本。期初效果都还不错，ping大概都在200以内。不过最近突然发现ping奇高无比。不明其究。无语。。。某天拿到了一些Google Cloud的coupon，异想天开，尝试用Google Cloud的虚拟机搭建了ss，竟然发现ping值低到出奇
！100ms以内，丢包率很低。发现网上相关教程较少，所以这里大概讲讲步骤吧。有不明白的同学给我留言即可。

##第一步是注册登录，

  没有账户的同学改进注册一个cloud服务的账户。一定要绑定自己的信用卡。因为绑定之后可以拿到300刀，60内有效的coupon哦~哈哈哈

![Login Console](/images/gcloud_ssserver/login_console.png)
<!--more-->
##第二步，建立工程
  
  注册之后进入到自己的控制台，console，就需要创建一个工程/project，当然，很多同学之前有建立Google API项目，在这里就能看到。建立完成之后就进入项目的。

![Create a project](/images/gcloud_ssserver/create_a_project.png)

##第三步，建立VM
  当你建立项目之后，选择该项目。然后再左边工具栏里面选择建立vm。

![Create VM](/images/gcloud_ssserver/create_vm.png)

我选择的是最基本的一个设置。用的是ubuntu 14的OS。另外，权限的各种设置什么的就和其他vps一样了。

##最后一步是最重要的，设置防火墙规则，

![Set up Firewall](/images/gcloud_ssserver/firewall.png)

这儿非常重要。否则你的ss是无法访问到的。设置既可以从UI上面找到，也可以使用命令。命令有点类似ufw，总之就是很简单很简答了。如下图，设置规则给你的端口。

![Add port to allow traffic](/images/gcloud_ssserver/allow_8388.png)

以上就是整个流程。如果有问题可以评论里面问我。
