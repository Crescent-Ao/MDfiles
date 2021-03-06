### C++ Primer 学习笔记

#### 练习2.3

```c
#include <iostream>
using namespace std;
int main()
{
    unsigned u1=42,u2=10;
    cout<<u1-u2<<endl;
    cout<<u2-u1<<endl;
    int i=10,i2=42;
    cout<<i2-i<<endl;
    cout<<i-i2<<endl;
    cout<<i-u2<<endl;
    cout<<u2-i<<endl;
}
```

运行结果

![image-20210124190733811](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210124190733811.png)

32没什么可说，后者的答案是这样的算的
$$
2^{32}-32=4294967264
$$
由于int是有符号数输出按正常加减法计算

![image-20210124191613397](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210124191613397.png)

#### 2.1.3字面值常量

每个字面值常量都对应一种数据类型，字面值常量的形式和值决定了它的数据类型

#####整型和浮点类型字面值

整型可以分为十进制（decimal),二进制（binary）,八进制（oct)，16进制（hex)。整型字面值的数据类型的确定，需要它的值和符号一起确定，要容纳下当前的值

浮点类型的字面值表现可科学计算法或者小数来表示的指数（E）

##### 字符和字符串型字面值

单引号括起来的一个字符称为char字面值，由双引号括起来的多个字符称为，字符串型字面值。字符串型字面值是由常量组成的数组array，编译器在每个字符串的结尾会加上‘\0’，因此字符串型字面值要比实际字符内容多1.”A”和’a’的位数就不相同了。

```c
'c'；
"Crescent is hard-working"
```

##### 转义序列

C++中带有特殊含义的字符（单引号、双引号、问好、反斜线等等）

##### 指定字面值的类型

对于一个整型字面值来说，我们能分别确定它是否带符号以及占用多少空间，后缀为u，则该符号值属于浮点类型，也就是说以U为后缀的十进制、八进制、16进制都将从unsigned int，unsigned long 和unsigned long long中选择一个匹配空间最小的一个作为数据类型。

##### 布尔字面值和指针字面值

```c
bool test=false;
bool test=True;都是布尔类型的字面值
nullptr为指针字面值    
 
```

#### 练习2.5

- ‘a’,L’a’,”a”,L”a”  字符字面值 wchar_t类型字符字面值 字符串型字面值 wchar_t类型字符串型字面值
- 10,10u,10L,10uL,012,0xc, 整型字面值 无符号整型字面值 长整型字面值 无符号长整型字面值 10进制整型字面值 16进制整型字面值
- 3.14,3.14f,3.14L 浮点字面值(default double) float型浮点字面值 long double浮点字面值
- 10,10u,10.,10e-2 整型字面值 无符号整型字面值 浮点字面值（point小数表示） 浮点字面值（科学计数法表示）全是double

#### 练习2.6

```c
int month=9.day=7;
int month=09,day=07;
```

不一样，右端字面值不一样,0代表八进制 month那个八进制无效因为没有9

##### 下面字面值有何种含义

1. Who goes with Fergus?(换行)，string 类型
2. 31.4 long double型
3. 1024f 无效 f只能用于浮点数
4. 3.14L long double型

##### 变量定义

一般来说（variance)和object一般可以共同使用，变量定义一般有类型说明符，随后紧跟着一个或多个组成的列表，变量名用逗号分隔，最后一分号结束

##### 默认初始化的问题

- 变量在没有被指定初值，则变量被默认初始化，默认值由变量类型决定
- 定义在函数体内部将不会被初始化
- 类的对象未被初始化，且初值根据类内部来定义

#### 练习2.9

```c
int input_value;
cin>>input_value;
int i={3.14};//正确但是数据会丢失
double i{3.14};
double salary=9999.99,wage=9999.99;
double salary=9999.99,wage;
wage=salary;
float i=3.14;   
```

```c
#include <iostream>
using namespace std;
string global_str;//全局变量
int global_int;
int main()
{
    int local_int;//函数体内部变量
    string local_str;
    cout<<global_int<<'\n'<<global_str<<'\n'<<local_int<<'\n'<<local_str<<endl;
}
```

![image-20210124214231300](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210124214231300.png)

##### 变量声明和定义的关系

声明使得名字为程序所知而定义负责创建与名字关联的实体

变量声明规定了变量的类型和名字，定义还申请存储存储空间有的时候也可能为变量

```c
extern int i;
int j;//声明而非定义
```

任何包含显示初始化的声明即成为定义。我们能给由extern关键字符一个初始值，这么做也就使得extern作用无效

#### 2.11

定义 定义 声明

##### 标识符

字母数字下划线，其中必须以字母或下划线开头，标识符的长度没有限制，但是大小写敏感

#### 复合类型

一条声明语句由一个基本数据类型和紧随其后一个声明符列表组成，每个声明符命名了一个变量并指定该变量与基本数据类型有关的某种的类型.

##### 引用

引用为变量起了另外一个名字

```c
int ival=1024;
int &refval=ival;//refval指向ival的名字
int &refval2;//错误
```

一般在初始化变量是，初始值会被拷贝到新建的对象中，定义引用时，程序会把初始值和引用绑定在一起。一旦初始化完成，引用将和它的初始值绑定在一起。

> 引用并非对象，引用只是变量的另外一个名字，即引用就是别名

```c
refval=2;
int ii=refval;//ival=2
```

获取引用的值，实际上获取了与引用绑定的对象的值，以引用作为初始值，实际上是以与 引用绑定对象作为初值值。

##### 引用的定义

引用类型的初始值必须是一个对象，此处引用类型的初始值必须与定义的数据类型相匹配

##### 练习2.15

- (b)和(d)都是错误的，因为引用要赋变量，和必须初始化

##### 练习2.16

- (a)合法 (b)不合法 数据类型不匹配 (c)同上（d)不合法

##### 练习2.17

- 两个都是10

#### 指针

指针类型匹配

```c
double dval;
double *pd=&dval;
double *pd2=pd;//指针的指针
int  *pi=pd;//指针类型不匹配
pi=&dval;//试图把double型对象的地址赋给int型对象
```

##### 指针值

1. 指向一个对象
2. 指向紧邻对象所占空间的下一个位置
3. 空指针，意味着指针没有指向任何对象
4.  无效指针，也就是上述情况之外的其他值

##### 空指针（nullptr)

不指向任何对象，在试图使用一个指针之前代码可以检查它是否为空，以下列出几个空指针的方法

```c
int *p1=nullptr;
int *p2=0;//初始化字面常量为0
int *p3=NULL;
i=0;
int *p1=i;//将int变量直接赋给指针是错误的操作，即使恰好等于0也不行
```

> 建议初始化所有的指针，即使不清楚该指针指向何处，就把它初始化为空指针或者尾0

##### 赋值和指针

指针和引用都能提供对其他对象的间接访问。一旦定义了引用，就无法令其再绑定到其他的对象，之后每次使用这个引用都是访问它最初绑定的对象。

赋值永远改变的是等号左侧的对象，当写出

##### 练习

```c
int main()
{
    int i=42;
    int d=32;
    int *pd=&i;
    pd=&d;//更改指针的值
    *pd=99;//更改指针所指向对象的值
    cout<<d<<" "<<i<<endl;
}
```

指针和引用的主要区别

指针实际上就是内存空间的地址，而引用可以说是小名

引用必须初始化，并且一旦定义了引用就无法再绑定到其他对象。而指针无须在定义时赋初值，也可以重新赋值让其指向其他对象。

代码的作用

将i更新值$ i^2$

(a)非法，因为指针的数据类型和变量的数据类型不匹配 (b)将变量赋给指针的操作时错误的(c)正确

判断P是否为空指针 判断p指向的对象是否为0

不能，因为首先要确定这个指针是不是合法的，才能判断它所指向的对象是不是合法的

因为void*型可以容纳所有对象的指针，而后者指针类型和变量类型不匹配所以不HEPA

##### 指向指针的指针

```c
int ival=1024;
int *pi=&ival;
int **ppi=&pi
```

##### 指向指针的引用

