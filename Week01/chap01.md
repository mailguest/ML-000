## Week01 - first day

### 环境搭建，各种安装：

### 一、build-essential安装

```
# gcc 版本实现C++标准不同，必须支持C++ 11标准
sudo apt-get install build-essential

# 如果您使用的是 Mac OS X，最快捷的获取 GCC 的方法是从苹果的网站上下载 Xcode 开发环境，并按照安装说明进行安装。一旦安装上 Xcode，您就能使用 GNU 编译器。Xcode 目前可从 developer.apple.com/technologies/tools/ 上下载。

# 查看gcc是否安装成功
gcc --version
```

### 二、CMake安装：

```
下载cmke https://cmake.org/download/
cd cmake-3.19.2
./bootstrap
'多少线程就是多少-j
make -j4
'安装
sudo make install
```

### 三、Anaconda安装：

```
https://www.anaconda.com
wget命令可以直接下载
individual edition
linux 64-bit
source ~/.bashrc

建议用miniconda，可以解决包冲突问题
一般建议用pip安装

用python3.7
3.6缺少包
3.8对pytouch不支持
conda install python==3.7

先安装难装的包，例如cuml
```

#### jupyter notebook安装：

[官网地址](https://jupyter-notebook.readthedocs.io/en/latest/examples/Notebook/examples_index.html)

```shell
conda install jupyter
```

### 四、R安装：

单独sudo apt-get install R可能影响问题，建议使用conda安装。注意：切记这里一定要关闭jupyter notebook后安装。

```
conda install r-essentials r-base
conda install -c r r-dplyr
```

#### 1. R优势 form 群消息整理

```
▶ R当中自动解决模型不可识别的问题，对于非线性变换 经常要用miss这个包进行填充。（缺失值是个大坑）

▶ 然后线性变量进行样条的时候你可以很方便调用。这些功能全部需要你在python中自己实现，预计代码在一万行左右，我自己实现了其中一个功能 就1000多行，而且由于实现效率比较低 还必须全部用C来写

▶ 除此之外，dplyr做数据探索极其方便(https://dplyr.tidyverse.org/)。比如说你们看这里的例子 这个东西要是pytorch来实现 代码量至少3倍

▶ 除此之外，bayes 网络可以自动告诉你哪些变量之间有一些关系，对于探索性分析很有帮助。这个比变量聚类效果很多，并且根据变量分类，可以使用lavaan包构建结构方程 从而构建子指标体系
```

#### 2. R优势 form ppt

```
▶ 操作方便:例如??dplyr 包当中可以实现迅速的数据探索性分析。

▶ 很多统计性常用的包:例如使用多重填充后用，GLM+ 样条 +L1 损失构造变量，这种特征构造对于和 线性模型有关的(例如深度学习)有很大关系。注意 R 当中不需要考虑模型不收敛问题，解决这个问题用 C(python 速度过慢)来写大概需要 1000 行(并且还 没考虑缺失值问题)

▶ 非预测性建模问题。见加餐。
```


#### 3. 安装方式2: 通过Rstudio

```
install.packages('devtools')
devtools::install_github('IRkernel/IRkernel')
IRkernel::installspec()
```

#### 4. 用来查看jupyter的kernal路径

```
jupyter kernelspec list
```

#### 5. 安装后就可以直接在jupyter notebook中使用了。

#### 6. 学习新语言步骤：

```
    * 变量和赋值。 
    * 控制循环。
    * 函数定义。
    * 类的定义。
    * 常见函数、数据结构。
```

### 五、Docker安装：

```
docker install ubuntu
微服务基本都是用docker
https://docs.docker.com/engine/install/ubuntu/
按命令往下走即可
post-install 
比较重要的命令 
docker pull hello-world 拉镜像
docker run -it --rm 进入系统
    -it:
    --rm:用完删除
    --gpus all:如果用了nvidia docker情况下用
    -v:将本地文件映射到docker的那个文件
    -p 8888:8888:将端口映射
    awesome_image:latest
```

### 六、NViDIA Docker安装：

```
cn.bing.com查询    
```

### 七、CUDA安装：

```
必须是N卡，非A卡。

版本选择:最新版或适合你的深度学习框架的版本。

注意:当host系统上的CUDA版本高于docker内的时候，可以进行运行反过来不行。
```

```
1. 不同系统不一样，需要查看不同命令。
disable nouveau

2. 重启系统并进入到 physical shell。ubuntu 的快捷键(可能是)CTRL+ALT+F2。

3. 关闭 xserver。命令可以有很多，例如 sudo init 3。

4. cuda download，去官网下载，必须选择runfile文件来安装。

5. 运行时候结尾加上–no-opengl-libs 命令。否则会造成登陆循环。
sudo sh cuda_11.2.0_460.27.04_linux.run --no-opengl-libs

     
注意:CUDA 安装十分危险。安装失败后补救措施一 般只能采用重装系统的方式。
```

### 八、IDE安装：

```
pycharm
fn + shift + F6 批量修改变量名
code -> reformat code 格式化代码
refactor -> extracl method 重构代码
调试
jupyter notebook
```

### 九、other

```
python / R 特性
R -> splus
dynamic-typing
高表现的用python
统计学的包用R

type-hint
def myfund(a:float, *args, **kwargs) -> str:
    return str(a)

monad
Dict无序，需要有序可以用OrderDict
可以通过**{}传参方式，把字典打开
可以通过*[]传参方式，把列表打开


* 贝叶斯

* 似然函数

* 神经网络

* lightgbm 
    * [看懂LightGBM](https://lightgbm.readthedocs.io/en/latest/)
    * [官网](https://lightgbm.readthedocs.io/en/latest/)

林元庆 
b-ok.org 没有找不到的tech books
Coursera
echidna
re0
Artificial intelligence a modern approach
```

### 十、非预测性建模：

* 对于没有真实的目标变量的建模，我们不会进行讲解(因为应用有限)。但我们想分析一下常见的一个例子。
* 场景：
    1. 提供违约报告，除去提供违约整体概率外，还想给出 不同维度上的得分。并且这些得分应该和模型基本一 致。
    2. 这种场景非常多。例如蚂蚁和京东都会卖一些分数 (由于数据需要脱敏)。
* 传统解决方法：
    1. 业务人员拍脑袋;单独拟合模型。基本得到结果没用。
    2. PCA 降维。存在问题:
        - ▶ 不能加入业务理解。 
        - ▶ 多重结构怎么办。 
        - ▶ 怎么得到得分
* 建议解决方案：
    1. 首先采用预测性建模，保证模型准确性。
    2. 采用 SHAP(Lundberg and Lee 2017)。SHAP 可以得到 具体变量的影响，其影响是从预测模型中蒸馏出来的， 所以一致性可以保证。并且因为 SHAP 是可加性模型， 所以多个子变量加起来也没问题。
    3. 但是多层指标体系怎么构建呢?
        - ▶ 首先采用 bayes 网络 (Jensen et al. 1996) 得到变量之间 互相影响的关系。这个可以使用 R 的 bnlearn(Scutari 2009).
        - ▶ 采用结构方程 (Hox and Bechger 1998)，结合业务知识， 构建多层指标(结构方程内部有评价模型好坏标准)。 这个可以用 R 的 lavaan 包 (Rosseel 2012) 实现。
* 核心：
    * 把无监督问题转化为有监督问题!!!
 


### 十一、预习内容：

* 第二周:对于有 C 基础的同学，请简单复习一下 C 的 内容和语法。没有基础不需要复习。
* 第三周:请阅读 All of Statistics(Wasserman 2013)，译本《统计学完全教程》。 注：看不懂地方请一定注明。
    * 1.概率
    * 2.随机变量
    * 3.数学期望
    * 6.模型、统计推断与学习
    * 9.参数推断
    * 11.贝叶斯推断


### 十二、参考文献：

* Hox, Joop J and Timo M Bechger (1998). “An introduction to structural equation modeling”. In:
* Jensen, Finn V et al. (1996). An introduction to Bayesian networks. Vol. 210. UCL press London.
* Lundberg, Scott M and Su-In Lee (2017). “A unified approach to interpreting model predictions”. In: Advances in neural information processing systems, pp. 4765–4774.
* Rosseel, Yves (2012). “Lavaan: An R package for structural equation modeling and more. Version 0.5–12 (BETA)”. In: Journal of statistical software 48.2, pp. 1–36.
* Scutari, Marco (2009). “Learning Bayesian networks with the bnlearn R package”. In: arXiv preprint arXiv:0908.3817.
* Wasserman, Larry (2013). All of statistics: a concise course in statistical inference. Springer Science & Business Media.
* mlapp esl 花书
* 黎曼几何
* [吴恩达的深度学习](https://mooc.study.163.com/smartSpec/detail/1001319001.htm)
* [《深度学习的数学》](https://www.bilibili.com/video/BV1LJ411g724?from=search&seid=3001564684542974225)
 