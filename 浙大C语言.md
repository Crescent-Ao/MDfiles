```c
#include<stdio.h>
int amount[]={1,5,10.25,50};
char *name[]={"pennt","nickel","dime","quarter","half-dolar"};
int search)int key,int a[],int len)
{
    int ret=-1;
    for(int i=0;i<len;i++)
    {
        if(key==a[i])
        {
            ret=i;
            break;
        }
    }
    return ret; 
}
int main()
{
    int k=10;
    int r=search(k,amount,sizeof(amount)/sizeof(amount[0]));
     if(r>-1)
     {
         printf("%s",name[r]);
     }
}
```

二分法的应用前提是数组是有效的

```c
int serach(int key,int a[],int len)
{
    int left=0;
    int right=len-1;
    while(left<=right)
    {
        int mid=(left+right)/2;
        if(a[mid]==k)
        {
            ret=mid;
            break;
        }
        else if(a[mid>k])
        {
            right=mid-1;
        }
        else
        {
            left=mid+1;
        }
    }
    return mid;
}
//所要搜素的数目为log2N
```

#### 数组排序

 ```c
int max(int a[],int len)
{
    int maxid=0;
    for(int i=1;i<len;i++)
    {
        if(a[i]>a[maxid])
            maxid=i;
    }
    return maxid;
}
//希望90放在最后，原来位置上的数要和90做交换，交换
int main()
{
    int a[]={0};//未做初始化
    int len=sizeof(a)/sizepf(a[0]);
    for(int i=len-1;i>0;i--)
    {
    int maxid=max(a,i+1);
        //swap(a[maxid],a[len-1])
        int t=a[maxid];
        a[maxid]=a[i];
        a[i]=t;
    }   
    for(int i=0;i<len;i++)
    {
        printf("%d",a[i]);
    }
    return 0;
}
 ```

## 指针和字符串

####指针

- sizeof运算符，给出某个类型或变量在内存中所占据的字节数
- sizeof(int)
- sizeof(i)

- 运算符&，获取变量的地址，必须是变量

```c
int main(void)
{
    int i;
    int p;
    p=(int)&i;//这是32位编译过
    printf("0x%x",&i);
    printf("%p",&i);//输出以地址方式输出
    return 0;
}
```

![image-20210506105707286](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506105707286.png)

第一个是32位编译的结果，第二个是64位编译的结果

所以前面是4个字节，后面是8个字节

- scanf(“%d”,&i)获取变量的地址，它的操作数必须是变量，地址的大小是否与int相同取决于编译器的位数，具体可以看上面的结果
- &不能取（a+b)(i++)(++i)必须有明确的变脸
- 32位的int类型占据四个字节
- stack区的自顶向下分配内存

scanf()的函数原型，需要一个参数保存别的变量的地址，如何表达能够保存地址的变量

- 指针就是保存地址的变量

  ```
  int *p=&i;
  int *p,q;//P是指针，q是int类型的变量
  ```

  也就是p->i，p的值指明的是i的地址

  #### 指针变量

  - 变量的值是内存的地址
  - 指针变量的值是具有实际值变量的地址

```c
void f(int *p);
int main(void)
{
    int i=6;printf("&i=%p\n",&i);
    f(&i);
    return 0
}
void f(int *p)
{
    printf("p=%p",p);
    printf("%d",*p);
}
//输出的结果是一样，f函数可以通过地址的方式访问或者改变外面的值    
```

![image-20210506154319428](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506154319428.png)

#### 解运算符

- *是一个单目运算符，用来访问指针的值，所表示地址上的变量

作为参数的指针

- void f( int **)

#### 指针和数组

传入函数的数组组成了什么?

```c
void minmax(int a[],int len,int *max,int *min)//传入的实际上是数组起始的指针变量；函数参数表的数组实际上是指针
{
    int i;
    printf("minmax sizeof(a)=%lu\n",sizeof(a));
    *min=*max=0;
    f
}
```

- sizeof(a)==sizeof(int *)
- 可以用数组的运算符[]进行运算

函数原型等价

- int sum (int *ar,int  n)
- int sum(int *,int)
- int sum(int a[],int n);

#### 数组变量是特殊的指针

- 数组变量本身表达就是地址
- int a[10];int *p；//无需使用取地址符*
- 数组单元表达的是变量，需要取地址符
- a==&a[0]

- []可以对数组做也可以做指针做
- p[0]==*p
- 数组变量是const指针，所以不能赋值
- int b[]=a;int *const b；常量指针,所以数组变量不能直接赋值

## 字符类型

- char 是一种证书，也是一种特殊的字符

- scanf和printf用%c来表示输入输出字符

- 字符‘1’和数组1是不相同的，字符字面量是以ASCII码存储的

  ``` 
  char c;
  int i;
  scanf("%c",&c);//scanf只能处理int不能处理char
  scanf("%d",&i;);
  c=i 
  printf("%c",c);
  printf("%d",c);
  ```

  ![image-20210506163417368](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506163417368.png)

#### 逃逸字符

#### 字符数组

char word[]=[‘H’,’e’,’l’,’l’,’o]不是字符串只能是字符数组

char word[]=[h,e,l,l,o,\0];

![image-20210506164504530](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506164504530.png)

字符串变量

- char *str=“Hello”

- char word[]=“Hello”

- char line [10]=“Hello”字符串的字面量编译器会生成结尾\0,这个数组实际上的长度为6

- 两个相邻的字符串常量会自动连接起来，中间没有任何其他的符号连接起来称为两个

  ![image-20210506165354164](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506165354164.png)

  

- C语言字符串是以字符数组形态存在的

  - 不能用运算符对字符串做运算
  - 通过数组的方式可以遍历字符串

  - 可以用字符串的字面量来初始化字符串

  #### 字符串变量

  char  *s=“Hello world”;

   ![image-20210506170013035](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506170013035.png)

字符串存在代码段，只读不能写

- s是一个指针，初始化指向一个字符串常量
- const char *s，不能改变字符串变量
- 如果要修改字符串，要使用数组
- char s[]=“Hello world!”

将字符数组在代码段的字符串的常量拷贝到数据段(可以改变的存在)

![image-20210506170614723](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506170614723.png)

![image-20210506170706855](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506170706855.png)

字符串的输入输出

- char string[8]
- scanf(“%s”,string)
- printf(“%s”,string)

- scanf读入一个单词(到空格、tab或者回车为止)，scanf是不安全的，因为不能知道读到的位置 

![image-20210506171935585](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210506171935585.png)

未读完的数据

- char *string;//未初始化，所以不一定每次运行都出错
- scanf(“%s”,string)
- char buffer[100]=“”
- 这是一个空的字符串，buffer[0]==‘\0’
- char buffer[]=“”;
- 长度为1

```c
#include<string.h>
```

- strlen size_t(const char *s)返回s的字符串的长度,不包括结尾的0. 不能改变字符串
- strcmp 比较字符串的大小,strcmp表明字符串是相等的 1大 -1小
- 数组的比较永远的是false，因为不是相同的地址
- 如果长度相等，则较长的为大，如果字符串长度相同的话，则按位比较
- strcpy(char *new,char *old)拷贝
- strcat (char *s1,char *s2);将s2拷贝到s1的后面，要保证 
- 要求有足够的变量求
- strncpy strncat 加一个n，可以指明最多拷过去多少的字符，如果超过则需要掐掉
- strncmp n只比较前几个
- char *strchr(const char *s,int c*);
- char *strchr(cons*

### 指针的应用

```c
void swap(int *pa,int *pb)
{
    int t=*pa;
    *pa=*pb;
    *pb=t;
}
```

- 函数返回多个值，某些值只能通过指针参数带回
- 传入的参数实际是要改变的值
- 函数传值仍然是传值，但是通过指针的作用，可以改变对应外部对应的外界的值
- 函数返回运算状态，结果通过指针返回
- 返回特殊不属于有效范围内的值来表示出错
- -1 或者 0
- 当任何数值都是有效的可能结果，就得分开返回

```c
int divide(int a,int b,int *result)
{
    int ret=1;
    if(b==0)ret=0;
    else
    {
        *result=a/b;
    }
    return ret;
}
```

## 指针与数组

- 传入函数的数组组成了实际上数组起始位置的地址
- 函数参数表中的数组实际上是指针
- sizeof(a)==sizeof(int *)
- 但是可以用数组的运算符[]进行运算

指针与const

- 指针--可以是const,值也可以是const
- int *const q=&i;//q是const
- q++ error
- const int *p=&i;所以指出指针所指向的值保持不变
- 不能通过p去修改，但是可以通过变量本身来改变对应值
- 当要传递参数的类型比地址大，可以较少的字节数给参数，又能避免外边对变量的修改
- consr int a[]={1,2,3,4,5,6};必须通过上述的方式进行初始化
- int sum(const int a[],int length)

### 指针运算

```c
char ac[]={0,1,2,3,4,5,6,7,8,9};
char *p=ac;
printf("P=%p",p);
printf("P+1=%p",p+1);
return 0;

```

- pointer的运算+1表明在原来地址上加上所指向的数据类型的大小sizeof(int)
- 递增++递减--
- 两个指针可以相减，不是地址的差，两个地址之间可以能放多少个sizeof的运算符
- *P++,取出所知的那个数据，然后顺便把p移动到下一个位置上去
- *的优先级没有++高
- 指针的比较运算符，实际上就是地址大小的比较
- 数组单元地址顺序递增排序

### 0地址

- 内存有0地址，0地址不能碰地址
- 0地址特殊的事情
  	- 返回的指针是无效的
  	- 指针没有被真正初始化
- NULL是预定定义的符号，表示0地址

### 动态内存分配

- C99可以用变量做数组定义的大小
- 动态内存分配 int *a=(int *)malloc(n**sizeof(int))

```c
#include<stdlib.h>
int main(void)
{
    int number;
    int *a;
    a=(int*)malloc(number*sizeof(int));
    return 0; 
}
```

![image-20210507154622856](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210507154622856.png)

```c
void *p;
while(p=malloc(100*1024*1024))
{
    cnt++;
}
printf("分配了%d00Mb\n",cnt);
return 0;
```

### free()

- 申请的空间还给系统
- free(NULL)
- 指针出来的话，初始化为0
- free(0)是不出错的
- 申请了free->长时间运行内存逐渐下降，内存漏洞或者内存垃圾
- 找不到合适的free时机
- 有malloc就必须有free

### putchar

- 向标准输出写一个字符
- 返回写了几个字符，EOF(-1)表示写失败

```c
while((ch=getchar())!=EOF)
{
    purchar(ch);
}
printf("EOF"\n);
```

$$ CTRL-C $$强制结束

$$ CTRL-Z $$强制结束 windows

keyboard-shell-screen 键盘上实际做的是行编辑，有很长的距离

### 字符串数组

- char**a
- a是一个指针，指针指向另一个指针，指针指向charde值
- char[][] \[a][b] 必须b设置
- char \*a[]

![image-20210507161656680](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210507161656680.png)

字符串数组的main参数

```c
int main(int argc,char const*argv[])
    argv[0]是命令本身;
{
    for(int i=0;i<argc;i++)
    {
        printf("%d:%d",i,argv[i]);
    }
```

### string.h

- strlen  返回字符串s的长度，不包含‘\0’

  ```c
  int mylen(const char *s)
  {
      int cnt=0;
      int index=0;
      while(s[index]!='\0')
      {
          index++;
          cnt++;
      }//重复l
          
  }
  ```

  ![image-20210508145753766](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508145753766.png)

- strcmp比较两个字符串
  -  0 s1==s2
  - 1 s1>s2
  - -1 s1<s2
  - 数组的比较永远是false

![image-20210508150623303](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508150623303.png)

```c
int mycmp(const char *s1,const char *s2)
{
    int index=0;
    while(s1[index]==s2[index]&&s1[index]!='\0')
    {
    //    if(s1[index]!=s2![index])
      //      break;
       // else if(s1[index]=='\0')
        //{
         //   break
        //}
        //idx++;
    }
    return s1[index]-s2[index];
    while(*s1==*s2&&*s1!='\0')
    {
        s1++;
        s2++;
    }
}

```

![image-20210508151301734](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508151301734.png)

### strcpy

将第二个参考拷贝的字符串，拷贝到第一个所指的空间中去

![image-20210508151420084](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508151420084.png)

函数原型 char \*strcpy(char \*restrict dst,const \*restricy src )

restrict  表明src和dst不重叠

把src的字符串拷贝到dst

返回dst

```c
char *dst=(char *)malloc(strlen(src+1));
strcpy(dst,src);
```

```c
char *mycopy(char *dst,const char *src)
{
    int index=0;
    while(src[index]!='\0')
    {
	    dst[idx]=src[idex];
        index++;
    }
    dst[index]='\0';
    return dst
}
```

```c
char *mycopy(char *dst,const char *src)
{
    char *ret=dst;
    while(*src)
    {
        *dst++=*src++;
    }
    *dst='\0';
    return retl
}
```

### 字符串中找字符

- char *strchr(conts char \*s,int c) 左边出现第一次位置返回的是指针
- char \*strrchr(const char *s,int c) 从右边返回的第一个位置
- 返回NULL

 ![image-20210508153230873](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508153230873.png)

```c
char *t=(char*)malloc(strlen(p)+1);
strcpy(t,p);
printf("%s",t);
free(t);  
```

![image-20210508153418521](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508153418521.png)

char *strstr(const char *s1,const char*\*s2)





## 结构类型

### 枚举

用符号而不是具体的数字来表示程序中的数字

```c
enum COLOR{RED,YELLOW,GREEN}
```

- 枚举用户定义的数据类型

- enum 枚举类型的名字{名字0,名字$ \dots$,名字n};他们就是常量符号，他们的类型就是int类型的值!!!!实际上是以整数做内部计算和外部输入输出的

- enum color{red,yello,green}

  ![image-20210508154525182](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508154525182.png)

  

![image-20210508154747291](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508154747291.png)

声明枚举量的时候可以指定值

- enum color{Red=1,yellow,Green=5}

枚举只是int，枚举很少使用，定义符号量而不是一种枚举类型来使用

### 结构类型

```c
struct date
{
    int month;
    int day;
    int year;
};//这个地方要有分号的
struct date today;
today.month=07;
today.day=31;
today.year=2014;
```

- 函数内部声明的结构类型只能在函数内部使用
- 通常结构生成在函数外面的地方，让所有的函数都能够使用

![image-20210508155659374](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508155659374.png)

![image-20210508155805389](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508155805389.png)

### 结构的初始化

```c
struct date today={07,31,2014};
struct date thismonth{.month=7,.year=2014};//默认为0
```

#### 结构成员

结构用.运算符和名字访问其成员

结构类型是虚的，结构变量为试题

#### 结构运算

- 访问结构，直接用结构变量的名字
- 赋值，去地址，也可以传递给函数参数
- p1=(struct point){5,10}
- p1=p2//p1.x=p2.x，数组变量无法做这种变化
- 和数组不同，结构变量的名字并不是结构变量的地址

![image-20210508160802580](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508160802580.png)

day=today;//完全是两个不同的东西，所以不是地址操作的

#### 结构与函数

![image-20210508162242922](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508162242922.png)

![image-20210508162653853](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508162653853.png)

arrow p所指的month

```c
struct point *getStruct(struct point *p)
{
    scanf("%d",&p->x);
    scanf("%d",&p->y);
    return p;
}
```

返回指针的作用，用来可以将此函数串到其他函数上去

![image-20210508163048015](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210508163048015.png)

*将函数返回的指针值，作为第一个变量来使用它

```c
*getstruct(&y)=(struct point){1,2}
```

### 内联

自定义数据类型，C语言提供一个叫做typedef 的功能

```c
typedef long int64_t;//第一个是原来的类型，第二个是新的名字
typedef struct AData{int month;int day;int year} Data;//第一个是原来的类型，第二个是新的名字
```

 ```c
typedef struct{int month;int day;inr year;} Date;
typedef char*String[10];//10个字符致和镇的数组
 ```

这样一个struct定义为Date,只有最后一个单词

### 联合 

```c
union AnElt{
    int i;char c
}alt1,alt2;
//这两个成员占用相同的空间变量
```

![image-20210512151025439](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210512151025439.png)

![image-20210512151135220](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210512151135220.png)

### 可变数组

- 可以长大的
- 可以得到当前的数组大小
- 访问数组中的元素

函数库(interface)

- Array array_create(int init_size);
- void array_free(Array \*a)
- int array_size(const array \*a)
- int \*array_at(Array *a,int index)
- void array_inflate(Array \*a,int more_size);

```c
typedef struct{int *array;int size;}Array;//只是一个结构而不是指针，不要定义定义出指针的类型，
typedef struct{int *array;int size;}*Array;//这种定义说明是指针
```

```c
Array array_create(int init size)
{
    Array a;
    a.size=init_size;
    a.array=(int *)malloc(sizeof(int)*init_size);
    return a;
}
void array_free(Array *a)
{
    free(a->array);
    a->array=NULL;free(0)和free(NULL)是无害的
    a->size=0;   
}
int array_size(const Array *a)
{
    return a->size;
}
//封装函数
int *array_at(Array *a,int index)
{
    if(index>=a->size)
    {
        //array_inflate(a,index-a->size+1);
        array_inflate(a,(index/BLOCK_SIZE+1)*BLOCK_SIZE-a->size)
    }
    return &(a->array[index]);
}
//如果返回的是指针，可以将值写到对应的数组
void array_inflate(Array *a,int more_size)
{
    int *p=(int *)malloc(sizeof(int)(a->size+more_size));
    for(int i=0;i<a->size;i++)
    {
        p[i]=a->array[i];
    }
    free(a->array);
    a-array=p;
    a->size+=more_size;
}
```

## 链表

![image-20210514123436301](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514123436301.png)

一部分数据，另外一部分是指针

![image-20210514123751141](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514123751141.png)

Linked-list   结点

```c
typedef _node{int value;struct _node *next;} Node;
```

```c
int main()
{
    int number;
    Node *head=NULL;
    do
    {
        scanf("%d",&number);
        if(number!=-1){
            //add to lined-List，加到结点是
            head=add(add &head,number);
         
    }while(number!=-1);
    return 0;       
}
```

### 链表的函数

```c
Node*add(Node *head,int number)
{
       Node *p=(Node*)malloc(sizeof(Node));
            p->value=number;
            p->next=NULL;
            //找到前面的最后一个
            Node *last=head;
            if(last)
            {
            while(Last->next)
            {
                last=last->next;
            }
            last->next=p;
            }
            else
            {
                head=p;//head 函数未修改
            }
        }
return head;
}
```

//第二种方法可以使用指针的指针

第四种方法

```c
typedef struct _list{
    Node*
} List;
```

![image-20210514130522186](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514130522186.png)

![image-20210514130615503](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514130615503.png)

![image-20210514130804648](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514130804648.png)

```c
Node *p;
for(p=list.head;p;p=p->next)
{
    printf("%d\t",p->value)
}
```

```c
void print(List *plist)
{
    Node *p;
    for(p=plist->head;p;p=p->next)
    {
        printf("%d\t",p->value);
    }
}
```

```c
for(p=list.head;p;p->next)
{
    if(p->value==number)
    {
        printf("找到了\n");
        break;
    }
}
```

![image-20210514132348775](C:\Users\王澳\AppData\Roaming\Typora\typora-user-images\image-20210514132348775.png)

```c
for(q=NULL,p=List.head;p;q=p,p=p->next)
{
    //链表不是空的，当在用指针的情况下，指针出现在arrow 的左边，这个时刻，这个指针不能是NULL
    if(p->value==number)
    {
        if(q)//第一个
        {
        q->next=p->next;
        }
        else
        {
            list.head=p->next;
        }
        free(p);
        break;
    }
}
//没有机制保证q不是null
```

### 链表的清除

for(p=head;p;p=q)

{

q=p->next;

free(p);

}