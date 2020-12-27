### C的复习笔记

[学习地址](https://www.runoob.com/cprogramming/c-tutorial.html)

#### 编译、运行
    1. create c file
```shell
cd ~/source/ccode
vim new.c
```
    2. input c code
```C
#include<studio.h>
int main(){
    printf("Hello\n");
    return 0;
}
```
    3. gcc c file & run c file
```shell
gcc new.c -o new.out
./new.out
```

#### 变量和赋值
```shell
vim add.c
```
```C
#include<stdio.h>
extern int x;
extern int y;
int add(){
    return x + y;
}
```
```shell
vim test.c
```
```C
#include<stdio.h>
int x = 1;
int y = 2;
int main(void){
    int result;
    result = add();
    printf("result is %d", result);
    return 0;
}
```
```shell
gcc add.c test.c -o main
./main
```

#### 控制循环

```C
for ( init; condition; increment ){
    dosomething(s);
}

// 无限循环
for ( ; ; ){
    dosomething(s);
}

while( condition ){
    dosomethin(s);
}

do{
    dosomething(s);
} while( condition );
```

#### 函数定义

```C
return_type function_name( parameter list ){
    dosomething...
}

// 函数声明
return_type function_name( parameter list);

// exp:
int max(int a, int b);
int max(int, int);


// 当您在一个源文件中定义函数且在另一个文件中调用函数时，函数声明是必需的。


// 函数指针
// 声明一个指向同样参数、返回值的函数指针类型
typeof int (*func_ptr)(int, int);

#include<stdio.h>

int max(int x, int y){
    return x > y ? x : y;
}

int main(void){
    int (* p)(int, int) = & max;// 这里&可以省略
    int a, b, c, d;
    
    printf("please input three numbers")
    scanf("%d %d %d", & a, & b, & c);
    
    d = p( p(a, b), c);
    
    printf("max num is %d", d);
    
    return 0;
}
```

#### 类的定义
#### 常见函数、数据结构

```C
// 复制字符串s2到s1
strcpy(s1, s2);
// s1拼接s2
strcat(s1, s2);
// s1字符串长度
strlen(s1);
// s1 s2比较，相同0，<返回<0,>返回>0
strcmp(s1, s2);
// ch第一次在s1出现的指针
strchr(s1, ch);
// s2在s1第一次出现的指针
strstr(s1, s2);

// 结构体：C 数组允许定义可存储相同类型数据项的变量，结构是 C 编程中另一种用户自定义的可用的数据类型，它允许您存储不同类型的数据项。
struct tag { 
    member-list
    member-list 
    member-list  
    ...
} variable-list ;

// 共同体：是一种特殊的数据类型，允许您在相同的内存位置存储不同的数据类型。您可以定义一个带有多成员的共用体，但是任何时候只能有一个成员带有值。共用体提供了一种使用相同的内存位置的有效方式
union [union tag]
{
   member definition;
   member definition;
   ...
   member definition;
} [one or more union variables];

// 位域：带有预定义宽度的变量被称为位域；如果程序的结构中包含多个开关量，只有 TRUE/FALSE 变量；
struct {
  unsigned int widthValidated;
  unsigned int heightValidated;
} status;

// typeof：C 语言提供了 typedef 关键字，您可以使用它来为类型取一个新的名字

typedef unsigned char BYTE;

// 在这个类型定义之后，标识符 BYTE 可作为类型 unsigned char 的缩写

BYTE  b1, b2;
```

#### typeof vs #define

```
#define 是 C 指令，用于为各种数据类型定义别名，与 typedef 类似，但是它们有以下几点不同：
typedef 仅限于为类型定义符号名称，#define 不仅可以为类型定义别名，也能为数值定义别名，比如您可以定义 1 为 ONE。
typedef 是由编译器执行解释的，#define 语句是由预编译器进行处理的。
```

#### 文件读写

```C
FILE *fopen( const char * filename, const char * mode );
int fclose( FILE *fp );
// 写
int fputc( int c, FILE *fp );
int fputs( const char *s, FILE *fp );
int fprintf(FILE *fp, const char *format, ...);
// 读
int fgetc( FILE * fp );
char *fgets( char *buf, int n, FILE *fp ); // 遇到一个换行符 '\n' 或文件的末尾 EOF，则只会返回读取到的字符，包括换行符
int fscanf(FILE *fp, const char *format, ...); // 遇到空格停止读取
// 二进制读写：通常是数组或结构体读写
size_t fread(void *ptr, size_t size_of_elements, size_t number_of_elements, FILE *a_file);    
size_t fwrite(const void *ptr, size_t size_of_elements, size_t number_of_elements, FILE *a_file);
```

#### 预处理

```
#define	 定义宏
#include 包含一个源代码文件
#undef	 取消已定义的宏
#ifdef	 如果宏已经定义，则返回真
#ifndef	 如果宏没有定义，则返回真
#if	     如果给定条件为真，则编译下面代码
#else	 #if 的替代方案
#elif	 如果前面的 #if 给定条件不为真，当前条件为真，则编译下面代码
#endif	 结束一个 #if……#else 条件编译块
#error	 当遇到标准错误时，输出错误消息
#pragma	 使用标准化方法，向编译器发布特殊的命令到编译器中
```

#### 预定义宏

```
__DATE__	当前日期，一个以 "MMM DD YYYY" 格式表示的字符常量。
__TIME__	当前时间，一个以 "HH:MM:SS" 格式表示的字符常量。
__FILE__	这会包含当前文件名，一个字符串常量。
__LINE__	这会包含当前行号，一个十进制常量。
__STDC__	当编译器以 ANSI 标准编译时，则定义为 1。
```

#### 预处理器运算符

```
宏延续运算符（\）
字符串常量化运算符（#）
标记粘贴运算符（##）
defined() 运算符
```

#### 参数化的宏

```
#define square(x) ((x) * (x))
#define MAX(x,y) ((x) > (y) ? (x) : (y))
```

#### 头文件

```
#include < > 引用的是编译器的类库路径里面的头文件。
#include " " 引用的是你程序目录的相对路径中的头文件，如果在程序目录没有找到引用的头文件则到编译器的类库路径的目录下找该头文件。
```