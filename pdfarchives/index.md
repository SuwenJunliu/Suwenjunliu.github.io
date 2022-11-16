

# 关于pdfArchives
这里主要存放一些已经整理成为pdf的文档。主要含有：

- 在大学/研究生期间写的大作业报告
- 已经发表的论文
- 其他一些不适合以blog形式发表的东西（例如对数学符号要求极高的内容，或者大篇幅的代码等）

这些pdf文档会简单的整理后排列在这个页面中。

# 作业报告

## 地震学

- 理论地震学作业报告———基于Matlab的神经网络地震事件检测

    此文基于Matlab的神经网络程序实现了一个非常小样本的机器学习，试图利用已经被Iris目录中记录的事件和一些“空事件”（或者说噪音）进行学习，从而找出部分未被记录的事件。本篇文章更多是试探性地进行研究，并且详细总结了Anaconda/ObsPy的用法，包括创建环境，下载事件等。适合一些从未使用过相关软件或者毫无使用基础的相关从业者进行参考。[文章下载地址](https://www.junliusw.cn/pdfarchives/苏文君柳-李远芳-地震学前沿课程实践.pdf)。

- 理论地震学作业报告———半无限空间Green函数推导和Matlab实现

    此文推导了Jonhson于1974年的半空间Green函数的解析表达式。主要思路是：对波动方程进行Laplace变换后，利用de Hoop变换，可以将积分表达式改写成沿着Cagniard-De Hoop积分路径的，新的积分表达式。而这个新的积分表达式恰好凑成Green函数的Laplace变换，从而直接得到Green函数。本文推导过程详细，图文并茂，并且修正了一些[张海明](https://sess.pku.edu.cn/szll/zzjzg/llyyydqwlyjss/269642.htm)老师Fortran程序中的Bug。[文章下载地址](https://www.junliusw.cn/pdfarchives/半空间格林函数求解.pdf)。


# 已经发表的论文

## 期刊论文

- The extended range phase shift method for broadband surface wave dispersion measurement from ambient noise and its application in ore deposit characterization

    论文基于在湖南沃溪地区的短周期仪器，利用改进的相移法提取频散并进行相关反演工作。[文章下载地址](https://www.junliusw.cn/pdfarchives/geo-2021-0320.1.pdf)。

- Joint Inversion of Receiver Function and Surface Wave Dispersion by Hamiltonian Monte Carlo Sampling,

    Python编写的HMC算法，用于接收函数和面波的联合反演。[文章下载地址](https://www.junliusw.cn/pdfarchives/srl-2022044.1.pdf)。程序开源在[Github](https://github.com/nqdu/RfSurfHmc)