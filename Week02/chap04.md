# chap04

just demo
```shell
mkdir build
cd build
cmake ..
make -j4
./c_example
```

just demo2
```shell
/opt/intel/vtune_profiler
source ./vtune-vars.sh
vtune-gui
```

just demo3
```shell
sudo gedit /proc/sys/kernel/pref_event_paranoid
sudo gedit /proc/sys/kernel/kptr_restrict

# CMakeList.txt文件打开OpenMP
```

## Cython用法
1. cython当c用
2. cython做数据预处理

## NumPy
```python
import numpy as np
cimport numpy as cnp

from scipy.stats import poisson
cnp.ndarray[double] # 需要注意指定类型,这样才能有效

@cython.boundscheck(False) # cython默认检测数组是否出界，这里可以关闭来提高性能
@cython.wraparound(False) # cython默认会包装方法，直接范围裸函数

double[::1] p_x # 直接传入指针，numpy中不一定存入指针
```

注意： numpy需要对齐,另外不是所有np都可以转成cnp的，以下这个用法必须在函数中才能有效。（原因未知）
```python
cdef cnp.ndarray[double, ndim=2, mode='fortran'] arg = np.asfortranarray(matrix, dtype=np.float64)
```
- 这句话意思就是，将numpy的数组复制到2维数组中，并默认np.float64，防止中间有空值出现。
- ndim=2 => 意思就是2维数组
- 矩阵存储：二维数组是指针的指针，int[名字N][月份M] 可能动态指针是不连续的，导致cache miss。在内存中会被拉成一位存储
- fortran 和 corder 的区别：fortran是把列存在一起。corder里面是把行存在一起
    - 如果对行取数操作，则建议以行储存mode = 'C'。例如：按人取数；np.ascontiguousarray()
    - 如果对列取数操作，则建议用mode = 'fortran'。例如：按月份取数; np.asfortranarray()

## cython和c的链接：connect_c
- path by copy 值传递
- path by point 指针传递
- path by refance 引用传递

## 一些建议
- Eigen 是C++库。
    - 其中 Eigen::Map
- simd: 用大的寄存器一次计算8个，在Eigen有这个解决方法。
- OpenMp对C++的class支持不好

## 并行和GIL
```python
ray init() # 最好全局调用
***_id = ray.put(****) # 这段可以节省时间
race condition
dask、ray都是多线程解决方案
```


## openmp：并行计算模块
- 对C++支持差，可以换用oneTBB
```python
from cython.parallel import prange
nogil
openmp只有prange
openmp 的cdef只用有c语法
setup中注意-fopenmp，linker_fliger解释.os文件需要链接
```

## 代码风格：
```md
pep8？ https://www.python.org/dev/peps/pep-0008/
```







