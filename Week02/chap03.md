# chap03

### 记住即可，不犯错，矩阵求导

#### 加餐

1. cv & nlp
2. c++优化
3. AI理论

#### 后续训练营

* nlp训练营
* cv训练营 -> 自动驾驶

#### python优化

1. python trick危险，要识别代码瓶颈，Profiler 的使用
2. 修改策略：算法本身收敛轮数、算法复杂度、hash设计不合理、内存顺序不合理、没有利用 simd
3. cython或者c++：内存/Cache/Register、SIMD
4. 并行（慎用）


* hotsports profiler实现: 
    * function profiler；好的profiler会告诉你：哪里慢，为什么慢？
    * line profiler；可以拆散profiler
    * 寻找原因：极其难。只能看到cpu/gpu表现，不能看到原因。
* 内存问题：内存(仓库-汽车) -> Cache(货架-飞机) -> Register(工作台-火箭)
    * 无法控制Cache：批读临近数据进Cache；数据不在一块读取耗时；
        * 例如：二为矩阵：长向量存储，row为存储？列循环时候就慢。如果行循环就很快
        * branch prediction，预判读取的if数据
        * 不同线程读同一段内存，可能导致时间长
        * cache miss（课题：hazelcast 2020）Cache-Miss-Rate
        * vtune-cookbook（2020）：vTune用于分析非常好用
* SIMD：
    * openMP指令（c/c++）需要注释实现
    * directory：相当于C当中的注释
    * intrinsics = 汇编
* random forest ； GPU不擅长if-else； 

* Target Encoding

* Cython
    * 区别：静态类/代码保护
    * C++文件 -> 编译.so文件: python setup.py -o2 install 
    
