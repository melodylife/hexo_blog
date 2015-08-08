title: "Google Tag Manager 使用"
date: 2015-08-07 01:36:02
tags: [GTM,Google Tag Manager,Usage,images/gtm-usage-1]
---

## 简介
Google Tag Manager, 简称GTM，是目前Google推出的web标签管理工具。这个工具看似不起眼，其实非常强队，尤其是对于做网站分析，推广，还有Google广告产品的重度用户。比如Adwords，GA又或者Double Click相关产品，甚至于一些非Google产品的标签都可以进行管理，比如LinkedIn等等。最近在折腾自己的Blog。为了提高逼格，特意用了Hexo。虽然Hexo的主题基本都原生支持了GA，但是依然觉得不是很放心，索性尝试了一下GTM，感觉非常不错，所以这里分享一点自己的经验给大家。希望能帮到大家。

<!--more-->
## 注册并安装Container
首先，注册GTM之后进入到GTM控制台，

![first-login image](/images/gtm-usage-1/first-login.png)

登陆之后，GTM会请你在Account下面建立一个Container。注意，Container一般是埋在head标签中

所以，只要这一段代码没有变化，你的网站就可以使用同一个Container。当然对于目前Web技术的发展，这是一个十分普遍的网站设计方式，可以重用很多网站代码。所以说，也可以理解为，一个Container就可以管理一个网站。如果一开始各位跟笔者一样糊涂，直接忽略了Container得代码框，没关系，请移步Admin这个分页，可以找到你刚刚创建的Container，点击*Install Google Tag Manager*即可呈现Container代码。

![find-container image](/images/gtm-usage-1/find-container.png)

将代码埋入需检测网站的以下标签中

```html
<head></head>
```
至此，布码就已经完成了。以后任何给页面添加新的网页标签，tag，都不用改动网页上面的代码了，很简单吧。那么我们看看如何实现用GTM实现GA pageview的功能。

## 实现GA Pageview

Pageview是GA最近被的功能。利用这个功能以前，还请大家先注册自己的GA账户。具体GA的使用方法，我们以后再讲，或者各位移步至GA页面观看教程即可。我们这里使用GTM的步骤如下。

1. 建立GA账户后，在Property下面，找到并记下Tracking ID

![GA tracking ID image](/images/gtm-usage-1/ga-tracking-id.png)

2. 跳回至GTM页面，进入Container分页，选择左侧边栏里面的*Tags*选项，选择*New*，就看到以下页面。

![GTM 4 GA](/images/gtm-usage-1/gtm-4-ga.png)

选择*Universal Analytics*,在*Configure Tag*下方的*Tracking ID*中填入刚刚在GA页面里面找到的*GA Tracking ID*，*Track Type*选项中，选择 *Page View*,然后继续下一步，在*Fire On*中选择*All Pages*,最后一步是用来设置出发的位置和条件的。因为我们这里是一个检测页面访问情况的标签，所以选择所有页面。最后保存即可。

![Configuration Done](/images/gtm-usage-1/conf-done.png)

创建并且保存之后，在*Tags*页面就会看到右上角有一个红色的*Publish*按钮。这个按钮就是把你刚刚的修改实施到网站上面。点击*Publish*之后，会跳出一个确认框。确认框下面可以选择直接实施，也可以选择预览，即，*Preview*，如果选择*Preview*，打开一个新Chrome浏览器Tab，访问已经埋有Container的页面，就可以看到浏览器窗口地步自动弹出一个Debug窗口，是不是超好用 :)。当然确认无误的话，可以直接选择*Publish*即可。这样你的页面就处理GA的监视之下了。

![Publish](/images/gtm-usage-1/publish.png)

最后，分享一个Chrome上面非常好用的小插件，可以查看任何网页上Google的状态。有了这个，你就可以时刻检查自己的GTM有没有偷懒了。

[Google Tag Assistant](https://chrome.google.com/webstore/detail/tag-assistant-by-google/kejbdjndbnbjgmefkgdddjlbokphdefk?utm_source=chrome-ntp-icon)


## 有用的链接
1. [GTM 网络课程](https://analyticsacademy.withgoogle.com/course05)，今年7.31号已经停止发放认证了，但是依然可以学习。
1. [Google Analytics](https://www.google.com/analytics), 目前安装最广泛的网站数据分析工具
1. [GTM 使用和注册页](http://www.google.com/tagmanager/)
