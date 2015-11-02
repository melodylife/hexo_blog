title: "如何使用GTM实现GA的Event Tracking"
date: 2015-08-15 22:18:54
tags: [GTM,Google Tag Manager,Usage,images/gtm-usage-2,Event Tracking]
---


##简介
前面的文章，我们大概了解了如何部署GTM的容器用以发射GA的Pageview的标签。很方便吧。其实GA的另一个重要功能，事件跟踪，也完全可以通过GTM实现。神奇的是，你根本不需要再去页面上部署任何代码，仅仅通过GTM的控制台设置就可以完成。简直再方便不过了。想想如今标签满布的页面，GTM这么给力，既可以省时省力又让我们的页面代码美观好看，何乐不为。这篇文章，通过一个例子，演示一下如何完成这样的设置。
<!--more-->
##目标
大家可以看到我的主页上每篇文章其实都是没有完全显示的，原因很简单啦，因为太长了，所以都加上了一个所谓 “Read More” 的按钮。方法很简单。都是markdown，只需要你在希望插入这么一个按钮的位置添加下面一行就可以实现了

```html
<!--more-->
```
![Readmore Button](/images/gtm-usage-2/require.png)


但是呢，我非常想知道，哪些用户点了这个按钮。同时也想知道是哪一篇文章。好吧，那我们就利用Google Analytics事件追踪吧。考虑到我页面上已经埋了GTM的容器，所以可以好好利用之。


##实现
###前提
在实现之前有一个前提必须搞定。因为这次我们需要追踪Click，所以需要一些Click相关的变量用作判断。所以首先enable 变量里面的所有Click变量是必须的。如下图，选择variable页面，然后选择所有的built-in的Click变量。这样的话GTM就可以从页面上搜集Click相关变量以供使用了。

![Enable Click Built-in Variables](/images/gtm-usage-2/enable-click-variable.png) 

###创建Trigger
  完成了以上的前提工作，我们开始实现。首先我们需要创建一个Trigger。这个Trigger会在实现Tag时候用到。选择Trigger页面，New，就会看到下图的UI了。选择Click，因为我们需要创建一个Click的事件跟踪。

![New Trigger](/images/gtm-usage-2/create-trigger-1.png)

接下来Target选择Links。这里建议选上waiting for tags 以及Check Validation。前者确保页面其它tag会顺利发出，后者确保不会有一些乱七八糟的点击产生。

![New Trigger and choose links](/images/gtm-usage-2/create-trigger-2.png)

接下来就到了激活条件了。可以看到在第一个下拉栏里面很多选项可供选择，甚至还能自定义。这里，因为我需要在主页上激活这事件追踪，所以我选择Page URL。然后我在比对方法里面选择了正则表达式。最后一栏写上正则表达式，完成。当然，你也可以添加更多的条件，不过注意，条件是与的关系哦。

![New Trigger and choose links](/images/gtm-usage-2/create-trigger-3.png)

最后一步Fire On选择Some Clicks，因为需要特定的点击才会触发追踪。这时候系统就会问你条件。我比较简单粗暴，直接选择Click Text，然后对应的就是 “Read More”

![Fire on](/images/gtm-usage-2/create-trigger-4.png)

###创建Tag
完成trigger之后tag就是轻而易举啦。建议直接Copy从前的pageview的tag，然后修改。理由很简单，首先这个tag被验证是可用的，另外GA的配置也没有改变。

![Copy Tag](/images/gtm-usage-2/config-tag-1.png)

设置Tag，把Tag类型修改为Event，这时候会跳出一些文本框让你填写，Category，是你事件的最大分类，因为事件是在主页发生的，所以我填了Home Page Events。Action就是具体时间的名称了，我填的Read More，再下去就是事件标签。当然是Click
的URL啦，很好区分。这些信息都会传给GA，你可以在GA里面进行一些操作打出非常好看的report。最后的Value不用填写，这个在eCommerce时候用的比较多。用来记录比如转化或者transaction价值之类的。

![Config Tag Event](/images/gtm-usage-2/config-tag-2.png)

这些搞定之后基本就算完成了。最后一步，一定要把AllPages删掉，选择Click,这时候会在弹出来的Trigger列表，选择我们刚刚定义的Trigger,完美。

![Remove AllPages](/images/gtm-usage-2/config-tag-3.png)


![Choose Trigger](/images/gtm-usage-2/config-tag-4.png)

###查看结果
最后publish所有的更改就搞定了。当然你也可以进入preview模式，但是Click事件调试不是很方便。最简单的办法，是去点一下对应的链接，然后去看GA的Real Time报告就可以验证了
![Real time report](/images/gtm-usage-2/real-time-report.png)

