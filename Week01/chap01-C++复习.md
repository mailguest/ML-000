### C++复习

[学习地址](https://www.runoob.com/cplusplus/cpp-tutorial.html)

#### 编译 & 执行

```shell
gcc main.cpp -lstdc++ -o main

g++ helloworld.cpp

g++ helloworld.cpp -o helloworld

g++ runoob1.cpp runoob2.cpp -o runoob

g++ -g -Wall -std=c++11 main.cpp
```

#### 头文件 & 输入输出

```C++
#include <iostream>
#include <cstring>
#include <ctime>
using namespace std;

cout << "XXX" << str << endl;
cin >> name >> age;
clog << "XXX" << str << endl;
cerr << "XXX" << str << endl;
```

#### 类

```C++
// 类的外部使用范围解析运算符 :: 定义该函数
class Box {
    public:
        double length;
        double breadth;
        double height;
    
        double getVolume(void);
}
double Box::getVolume(void) {
    return length * breadth * height;
}

// 继承
class Other {...};
class Animal {...};
class Dog : public Animal, public Other {...};
// 虚继承
class D{.....};
class B: virtual public D{......};
class A: virtual public D{......};
class C: public B, public A{.....};

// 与类同名的函数是构造函数。
// ~ 类名的是类的析构函数。
// 纯虚函数
class D {
    public:
        D(){ cout << "D()" << endl; }
        ~D(){ cout << "~D()" << endl; }
        // = 0 告诉编译器，函数没有主体，上面的虚函数是纯虚函数。
        virtual int area() = 0;
};
```

#### 文件读写

```C++
/*
ofstream	该数据类型表示输出文件流，用于创建文件并向文件写入信息。
ifstream	该数据类型表示输入文件流，用于从文件读取信息。
fstream	该数据类型通常表示文件流，且同时具有 ofstream 和 ifstream 两种功能，这意味着它可以创建文件，向文件写入信息，从文件读取信息。
*/
void open(const char *filename, ios::openmode mode);

/*
ios::app	追加模式。所有写入都追加到文件末尾。
ios::ate	文件打开后定位到文件末尾。
ios::in	打开文件用于读取。
ios::out	打开文件用于写入。
ios::trunc	如果该文件已经存在，其内容将在打开文件之前被截断，即把文件长度设为 0。
*/
// 如果您想要以写入模式打开文件，并希望截断文件，以防文件已存在
ofstream outfile;
outfile.open("file.dat", ios::out | ios::trunc );
// 如果想要打开一个文件用于读写，可以使用下面的语法：
ifstream  afile;
afile.open("file.dat", ios::out | ios::in );

// 关闭
void close();

// 文件指针
// 定位到 fileObject 的第 n 个字节（假设是 ios::beg）
fileObject.seekg( n );
 
// 把文件的读指针从 fileObject 当前位置向后移 n 个字节
fileObject.seekg( n, ios::cur );
 
// 把文件的读指针从 fileObject 末尾往回移 n 个字节
fileObject.seekg( n, ios::end );
 
// 定位到 fileObject 的末尾
fileObject.seekg( 0, ios::end );
```

#### 动态内存

```C++
new data-type;
//exp:
double* pvalue  = NULL; // 初始化为 null 的指针
pvalue  = new double;   // 为变量请求内存

// 释放 pvalue 所指向的内存
delete pvalue;
```

#### 命名空间

```C++
namespace namespace_name {
   // 代码声明
}
name::code;  // code 可以是变量或函数

// exp:
#include <iostream>
using namespace std;
 
// 第一个命名空间
namespace first_space{
   void func(){
      cout << "Inside first_space" << endl;
   }
}
// 第二个命名空间
namespace second_space{
   void func(){
      cout << "Inside second_space" << endl;
   }
}
int main ()
{
 
   // 调用第一个命名空间中的函数
   first_space::func();
   
   // 调用第二个命名空间中的函数
   second_space::func(); 
 
   return 0;
}
```

#### 信号处理

```C++
void (*signal (int sig, void (*func)(int)))(int); 
signal(registered signal, signal handler);
```

#### 多线程

```C++
#include <pthread.h>
pthread_create (thread, attr, start_routine, arg);
/*
thread	指向线程标识符指针。
attr	一个不透明的属性对象，可以被用来设置线程属性。您可以指定线程属性对象，也可以使用默认值 NULL。
start_routine	线程运行函数起始地址，一旦线程被创建就会执行。
arg	运行函数的参数。它必须通过把引用作为指针强制转换为 void 类型进行传递。如果没有传递参数，则使用 NULL。
*/
    
#include <pthread.h>
pthread_exit (status);

// 连接和分离线程
pthread_join (threadid, status) 
pthread_detach (threadid) 
```

多线程编译需要如下：

```shell
g++ test.cpp -lpthread -o test.o

g++ -Wno-write-strings test.cpp -lpthread -o test.o
```

#### web编程

```C++
// CGI
```