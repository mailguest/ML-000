# Cython学习笔记

### 前言

此文以自己学习cython理解基础上，整理的自己思路和操作步骤。如有有读到感觉非常奇怪，晦涩或不通的地方。也欢迎以任何途径找我交流，我会尽力改改，多谢。

### Cython是什么

可以看看[cython官网网站](https://cython.org/)

白话Cython就是一个静态编译器，可以将python翻译成C或C++的源码，然后在编译成可执行文件。他的特点，可以让C或C++在执行阶段调用python函数，也可以让python调用C或C++函数或属性。这样可以将Cython包装为外部C库，嵌入现有的python程序中，以提高python的代码执行速度。

### Cython的安装

Cython的安装。官网有很多安装方式，可以pip安装，可以下载后python install安装的。因为我这里的环境使用conda搭建的，这里就用了conda的安装举例：（注：conda安装包过程中默认会提示“<B>Proceed ([y]/n)?</B>”，一路y即可）

```shell
# 用conda创建一个新的env，取名为cython
conda create -n cython

# 切换到cython的env环境
source activate cython

# 用conda安装，python3.7
conda install python==3.7

# 这步才是真真的安装cython步骤
conda install cython
```

### Cython编译及编写

接下来我们可以开始编写Cython代码了，在编写代码之前先讲讲编译步骤。前文讲过Cython的编译步骤分为2步：
1. 将*.pyx文件编译为.c或者.cpp文件。（.c文件为C语言的源码文件，.cpp文件为C++语言的源码文件）
2. 再将.c/.cpp文件编译为.so文件（看官网说在windos下会编译为.pyd文件，这里笔者用的是mac没有验证过不知道哈。）
编译

```python

```

后续待完善……