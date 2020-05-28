



# 前言
由于我今天从拼多多上购入了新的笔记本，炫龙M7，CPU为Ryzen5-3600，GPU为RTX2060，正好我的旧电脑已经服役了三年，于是打算将新电脑作为之后三年地震学研究的工作站，因此安装Ubuntu系统，最新的系统为20.04。在安装过程中遇到了一些驱动问题，因此特别写这篇博文阐述故障发生和排除方法


# Ubuntu20.04的安装
在[Ubuntu官网](https://cn.ubuntu.com/download)可以找到Ubuntu 20.04，之后利用[Ultraiso](https://cn.ultraiso.net/)等软件将镜像写入u盘中即可。根据笔记本的不同，按相应的方法进入BIOS（此电脑为F2）,选择从U盘启动即可。

## 遇到的问题
在Ubuntu安装时，发现选择"Ubuntu"选项后，会花屏，具体表现为屏幕全黑，在上方约1/4处，有紫色条纹。此时由于没有提示，只能强行断电后重启。判断可能是显卡驱动有问题，在20.04版本中，提供了"Safe Graphic"，本质上是将Grub的启动项中，添加了"nomodeset"选项，即原本的

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
```

变成了

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
```

nomodeset的作用可以参考[What does nomodeset do](https://askubuntu.com/questions/207175/what-does-nomodeset-do)，即告诉内核不要加载显卡而用BIOS模式，这样就能避免花屏。之后正常安装即可。

### 新的问题

安装结束后，由于安装Linux之后，发现Win系统无法检测，导致没有Grub选项，默认的Grub是不显示菜单的，导致我想加入nomodeset选项都不行。尝试更换Centos或者Ubuntu18.04，故障依旧。最后用了一个比较傻的办法，在有Ubuntu 20.04的前提下，继续安装Ubuntu18.04，拥有双系统后，自然就出现了Grub菜单，在启动时点击c，修改启动项的内容，在``quiet splash``后添加``nomodeset``即可，这样就能正常进入系统了。

## 驱动的安装




# 文章历史
-  2019-05-28 第一次发布，解决Ubuntu20.04安装后花屏的问题。