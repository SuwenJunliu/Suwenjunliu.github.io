
# Before the beginning
最开始的时候，网站采用hexo搭建。但是在使用过程中出现了以下的问题

- 每次[Hexo](https://hexo.io/)编译的时间过长，本来改动特别小（可能只有一篇文章的一点东西改动）就要重新生成和部署一次，等待的时间从20秒到2分钟不等,但是[Hugo](https://gohugo.io/)编译的速度就要比Hexo快很多。
- 基于Hexo的[Even](https://github.com/ahonn/hexo-theme-even)主题和Hugo的[Even](https://github.com/olOwOlo/hugo-theme-even)主题相比，明显是Hugo的主题更加的好看，并且有很多新增的功能。

基于上述两点考虑，我最后决定迁移到Hugo之中。

# Hugo的安装和使用

## Windows版本

与Hexo类似，需要安装Hugo。

Hugo可以在Hugo的Github [Releases](https://github.com/gohugoio/hugo/releases)中找到。截至2020年2月2日，最新的版本是V0.63。[hugo_0.63.2_Windows-64bit.zip
](https://github.com/gohugoio/hugo/releases)。

{{% admonition warning "warning" %}}
有趣的是，这个Blog采用的Even主题，如果用了hugo_0.63.2_Windows-64bit.zip，就会让我的主页丢失。我不太确定是什么引起的，如果不是extended版本似乎就不会这样。
我目前使用的版本是v0.55.6，在这个版本下，Hugo编译的结果是正常的。
{{% /admonition %}}

下载解压后，可以发现里面只有一个hugo.exe文件。请将它解压到一个非中文目录下。例如：

``
E:\blog\hugo
``

接着，将这个路径添加到系统环境变量中。在Win10下，可以选择：
1. 对开始菜单右键，选择设置
2. 在打开的windows设置中，在“查找设置”对话框中输入“编辑系统环境变量”
3. 在打开的系统属性中，点击环境变量，在系统变量中找到“Path”，点击编辑。在弹出的“编辑环境变量”中，加入hugo.exe所在的目录。在本例中，为“E:\blog\hugo”（不包括引号内容）

如果已经成功添加环境变量，打开cmd，输入

```
hugo version
```

可以得到类似下边的输出

``
Hugo Static Site Generator v0.55.6-A5D4C82D windows/amd64 BuildDate: 2019-05-18T07:57:00Z
``

那么证明Hugo已经安装完成，可以正常使用。

# 主题的挑选和下载
该Blog选择了Even主题，可以参考[Even-Hugo](https://github.com/olOwOlo/hugo-theme-even/blob/master/README-zh.md)进行安装。

编译安装之后，一般需要修改config.toml以便进行个性化

# 关于该Hugo主题下的一些Tips

## 增加导航菜单按钮

若想增加导航菜单，可以修改config.toml
```
[[menu.main]]             # config your menu              # 配置目录
  name = "Home"
  weight = 10
  identifier = "home"
  url = "/"
```

配置相应的menu。例如，我想添加pdfArchives标签页，那么只需要在这段后边添加
```
[[menu.main]]
  name = "PdfArchives"
  weight = 50
  identifier = "pdfArchives"  
  url = "/pdfArchives/"
```
即可，其中weight指的是排序的权重。这个数字越小，就会在整个菜单栏中排越前边。

## Bat脚本进行推送

如果利用git，可以较为轻松的实现一键部署。此Blog采用的bat脚本如下
```
hugo --theme=even --baseUrl="https://Suwenjunliu.github.io/"
cd E:\blog\hugo-blog\junliusw.cn\public
git init
git remote add origin https://github.com/Suwenjunliu/Suwenjunliu.github.io.git
git add -A
git commit -m "commit"
git push -u origin master -f
cd E:\blog\hugo-blog\junliusw.cn
```