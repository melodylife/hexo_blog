title: "如何找到openwrt/pandorabox的可使用的源"
date: 2015-06-12 12:37:22
tags: [openwrt,package source,xiaomi mini,pandora]
---

最近倒腾了一下家里的小米路由器mini，装上了pandora，但是竟然发现无法安装curl。可能是从前的源里面没有curl吧。
但是苦于找到合适的源适中没有curl可以用，这是很痛苦的。
经过仔细观察，我还是解开了这个问题。找到合适的源步骤如下

1. 如果你的路由器在刷openwrt/pandorabox之后无法顺利运行以下命令，说明你的源配置有问题  
<code>opkg update</code>   
1. 请先备份源配置文件  
<code>cp /etc/opkg.conf /etc/opkg.conf.bak</code>  
1. 进入路由器配置页面，找到系统->软件包->配置 将所有的源删掉  
1. 进入以下网址  
<code>http://downloads.openwrt.org.cn/</code>  
1. 可以挨个文件夹搜索带有 Packages.gz  的文件夹，看看里面是否有你需要的软件包  
1. 如果有，则将此文件夹的地址复制到路由器软件包的源配置中。一行软件源配置，分为三个部分，前两个部分基本可以和原先配置相同。仅仅修改链接地址即可。比如我增加了一行如下。  
<code>src/gz base http://downloads.openwrt.org.cn/PandoraBox/ralink/packages/base</code>
1. 保存更改，在软件包->动作里面选择刷新列表，或者命令行输入以下命令刷新软件包列表，就可以在 可用软件包 选项中找到新配置的源下面的所有软件包了  
1. 此时可以在此处点击安装或者进入命令行用命令安装软件包  
