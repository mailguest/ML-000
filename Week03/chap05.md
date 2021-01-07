# chap05

为什么不用spark做？机器学习
spark不适合用于建模，hadoop之上的动作体系，计算速度依赖于用什么数据源
框架比较重，简单测试启动会比较慢，大数据量ok


* NumPy：矩阵（Tensor）处理工具
* Jax：NumPy+
* Pandas：一般数据处理工具。数据放在内存中，跑的会比较快
* dplyr：探索性数据分析工具
* Matplotlib：
* TensorBoard：

难点：
* Einsum 和 Broadcast 转换
* Jax

reshape
broadcastable

JAX
JIT + Jaxpr + Async Dispatch + XLA
tf => 静态图
deepmind
即时编译 JIT
异步图 Async Dispatch
XLA
leetcode
老师木：https://www.jiqizhixin.com/articles/2020-04-01-10
陈天奇团队的开源TVM老师
mindspore
paidoupaidou
niit