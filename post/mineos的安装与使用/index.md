
# 前言

由于科研需要，现在正在做一些格林函数张量（Green's Function）的计算。现在还是 Follow Zhao et al., 2011的思路做这方面的工作。因此需要学习Mineos的操作和使用。为了能够摆脱受制于人的局面，最终还是要重新构建整个框架，那就从公开的东西开始做吧。

# Mineos的安装

现在使用的Mineos版本是CIG公开的，[地址在这里](https://github.com/geodynamics/mineos)，如果找不到了应该也能从我的Githuh上头找到Fork的仓库。


## 一些前置的安装包
- autoconf
- lyx
- epstopdf

他们可以使用 

```
sudo apt-get install autoconf lyx texlive-font-utils
```

进行安装。



## 具体流程

```
git clone https://github.com/geodynamics/mineos.git
cd mineos
autoreconf --install
./configure
```

就可以完成安装了。

### 可能的一些问题

- 生成LaTex文档的时候出现：

        lyx --export pdf2 doc/mineos.lyx
        convert-im6.q16: not authorized `pdf:/tmp/lyx_tmpdir.MwNyJvV10002/lyx_tmpbuf0/12_media_kevin_junliu_mineos_doc_Figures_Fig2.pdf' @ error/constitute.c/WriteImage/1037.
        /usr/share/lyx/scripts/convertDefault.py ERROR
        Execution of "convert" failed.
        support/Systemcall.cpp (291): Systemcall: 'python -tt "/usr/share/lyx/scripts/convertDefault.py" ps "/tmp/lyx_tmpdir.MwNyJvV10002/lyx_tmpbuf0/12_media_kevin_junliu_mineos_doc_Figures_Fig2.eps" pdf "/tmp/lyx_tmpdir.MwNyJvV10002/lyx_tmpbuf0/12_media_kevin_junliu_mineos_doc_Figures_Fig2.pdf"' finished with exit code 1
        Error: Cannot convert file

    这个是 **ImageMagick** 的权限设置问题，可以参考这个 [StackOverflow](https://stackoverflow.com/questions/52861946/imagemagick-not-authorized-to-convert-pdf-to-an-image) 上的说明，调整对应的权限。我解决的方法是：修改 **ImageMagick** 对应的权限设置，即修改 

    ```
    /etc/PATH_OF_IMAGESMAGICK/policy.xml
    ```

    在我的环境下路径是 

    ```
    /etc/ImageMagick-6/policy.xml
    ```

    找到

    ```
    <policy domain="coder" rights="none" pattern="PDF" />
    ```

    将其修改为

    ```
    <policy domain="coder" rights="read|write" pattern="PDF" />
    ```





# 参考文献

Zhao, L. and Chevrot, S. (2011), An efficient and flexible approach to the calculation of three-dimensional full-wave Fréchet kernels for seismic tomography—I. Theory. Geophysical Journal International, 185: 922-938. https://doi.org/10.1111/j.1365-246X.2011.04983.x



# 文章历史

-  2022-11-16 第一次发布，并且一直在修改中。
