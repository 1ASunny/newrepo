stl·string 

1.输入

getline(cin,s);换行结束

getline(sin,s7,'a')直到'\n'结束

2.对象操作

s.empty()  判断是否为空，bool型

s.size() 或 s.length() 返回字符的个数

s[n]  返回位置为n的字符，从0开始计数

s1+s2 连接，看下面例子：

    可用此方法给字符串后面添加字符如：s=s+'a'; 
    
    a:  string s2=s1+", ";  //对，把一个string对象和一个字符面值连接起来是允许的
    
    b:  string s4="hello "+", ";   //错，不能将两个字符串面值相加
    
    c:  string s5=s1+", "+"world";   //对，前面两个相加相当于一个string对象；
    
    d:  string s6="hello" + ", " +  s2;  //错

（注：字符串尾部追加还可用s.append("abc")函数添加）

s1=s2  替换

s1==s2  相等，返回true或false

!=,<,<=,>,>=  字符串比较，两个字符串短的与长的前面匹配，短的小于长的

 

3:string对象中字符的处理（头文件cctype）

    isalnum(c)  如果c是字母或数字，返回 true
    
    isalpha(c)  如果c是字母，返回true
    
    iscntrl(c)  c是控制符，返回true
    
    isdigit(c)  如果c是数字，返回true
    
    isgraph(c)  如果c不是空格，则可打印，，则为true
    
    islower(c)  如果c是小写字母，则为true
    
    isupper(c)  如果c是大写字符，则为true
    
    isprint(c)  如果c是可打印的字符，则为true
    
    ispunct(c)  如果c是标点符号，则为true
    
    isspace(c) 如果c是空白字符，则为true
    
    isxdigit(c) 如果c是十六进制数，则为true
    
    tolower(c) 如果c是大写字符，则返回其小写字母，否则直接返回c
    
    toupper(c)  跟tolower相反

4：string对象中一些函数

/*-------------------------插入函数----------------------------------包括迭代器操作和下标操作，下标操作更灵活*/

s.insert( it , p );  把字符串p插入到it的位置

s.insert(p,n,t)；   迭代器p元素之前插入n个t的副本

s.insert(p,b,e);      迭代器p元素之前插入迭代器b到e之间的所有元素

s.insert(p,s2,poe2,len); 在下标p之前插入s2下标从poe2开始长度为len的元素

s.insert(pos,cp,len);  下标pos之前插入cp数组的前len个元素。

/*-----------------------替换函数-------------------------------*/

s.assign(b,e);  用迭代器b到e范围内的元素替换s

s.assign(n,t)；  用n个t的副本替换s

a.assign(s1,pos2,len);从s1的下标pos2开始连续替换len个。

s.replace ( 3 , 3 , " good " ) ;   从第三个起连续三个替换为good

s.substr(i,j)表示的是从索引位置i开始，连续的j个字符组成的字串  //string::npos  判断字符串是否结束

/*-----------------------删除函数-----------------------------*/

s.erase( 3 )||s.erase ( 0 , 4 ) ;  删除第四个元素或第一到第五个元素

/*----------------------其他函数-----------------------------*/

s.find ( " cat " ) ;  超找第一个出现的字符串”cat“，返回其下标值，查不到返回 4294967295，也可查找字符；

s.append(args); 将args接到s的后面

s.compare ( " good " ) ;  s与”good“比较相等返回0，比"good"大返回1，小则返回-1；

reverse ( s.begin(), s.end () );  反向排序函数，即字符串反转函数

函数名	描述
begin	得到指向字符串开头的Iterator

end	得到指向字符串结尾的Iterator

rbegin	得到指向反向字符串开头的Iterator

rend	得到指向反向字符串结尾的Iterator

size	得到字符串的大小

length	和size函数功能相同

max_size	字符串可能的最大大小

capacity	在不重新分配内存的情况下，字符串可能的大小

empty	判断是否为空

[  ]、at	下标访问，取第几个元素，相当于数组

c_str	取得C风格的const char* 字符串

data	取得字符串内容地址

operator=	赋值操作符

reserve	预留空间

swap	交换函数

insert	插入字符

append	追加字符

push_back	追加字符

+=	+= 操作符

erase	删除字符串

clear	清空字符容器中所有内容

resize	重新分配空间

assign	和赋值操作符一样

replace	替代

copy	字符串到空间

find	查找

rfind	反向查找

find_first_of	查找包含子串中的任何字符，返回第一个位置

find_first_not_of	查找不包含子串中的任何字符，返回第一个位置

find_last_of	查找包含子串中的任何字符，返回最后一个位置

find_last_not_of	查找不包含子串中的任何字符，返回最后一个位置

substr	得到字串

compare	比较字符串

+	字符串链接

==	判断是否相等

!=	判断是否不等于

< 、 <= 、 >=  、>	判断是否小于、小于等于、大于等于、大于

>>	从输入流中读入字符串

<<	字符串写入输出流

getline	从输入流中读入一行
原文链接：https://blog.csdn.net/weixin_43736974/article/details/84562337

count：使用方法是count（begin，end，‘a’），其中begin指的是起始地址，end指的是结束地址，第三个参数指的是需要查找的字符。

##选择部分函数进行赋值 ##
一、memset()
C/C++通用

1.头文件
C：#include<string.h>

C++：#include<cstring> or #include<string.h>

2.函数原型
【作用】：将已开辟内存空间_Dst的首_Size个字节的值设为值_Val。

void *memset(void *_Dst, int _Val, size_t _Size)
1
【例子】：

int a[5];
memset(a, 0, sizeof(a));
1
2
【解析：memset函数是以字节为单位进行赋值的】

取值过程：取表示值的_Val参数的一个低位字节Byte。
我们都知道int类型是4个字节，一个字节Byte是8bit。比如例子中传入0，其实是0x0000 0000（00000000 00000000 00000000 00000000），十六进制下的一位表示4位bit，即两位十六进制表示一个字节。取得就是0x0000 00 00 (00000000 00000000 00000000  00000000 ) \text{0x0000 00\boxed{00}(00000000 00000000 00000000 \boxed {00000000})}0x0000 00 
00

 (00000000 00000000 00000000  
00000000
 )。
同理，-1是0xffff ffff（11111111 11111111 11111111 11111111），而511是0x0000 01ff（00000000 00000000 00000001 11111111）的后八位都为0xff（11111111)，所以int a[5]赋值memset(a, -1, sizeof(int)*5)与memset(a, 511, sizeof(int)*5)所赋值的结果是一样的都为-1。
赋值过程
将_Val取的一个低位字节为单位，填充满所要初始化的空间。比如上面的例子中用0赋值得到数组元素都是0，就是因为a[0]就是用赋值了四个0x00字节，组合到一起刚好又是0。
【解析：_Dst就是地址位置】
这东西就是获得一个指向开始位置的地址嘛，那么就是获得数组的首地址的那几种方法嘛。

3.使用
（1）赋值int数组
如果用int类型赋值的话，要取每个字节都相同的值，因为别的值因为字节拆分组合起来就不是本身了。

比如用0或-1初始化，用0x3f3f3f3f（表示ACM中的无穷大）。

int a[5];

memset(a, 0, sizeof(a));
memset(&a[0], 0, sizeof(a));
memset(a, 0, 5 * sizeof(int));

int a[5][5];

memset(a, 0, sizeof(a));
memset(a[0], 0, sizeof(a));
memset(&a[0][0], 0, sizeof(a));
memset(a, 0, 25 * sizeof(int));
（2）赋值char数组
如果用char类型赋值的话，就是char本身。

因为char类型可以表示为ASCII码表示的int值，比如A就是65。

一般是赋值'\0'，'0'，'1'之类的（要加单引号）。

char a[5];
memset(a, 'A', sizeof(a));
for (int i = 0; i < 5; i++)
{
    cout << a[i] << " ";
}
cout << endl;
// A A A A A

（3）结构体
结构体也是按照字节为单位存储的

/* 一般的结构的清空操作 */
struct Student
{
    char name[16];
    int id;
};
struct Student Tom;
// 因为char数组只要出现'\0'就代表结束了
Tom.name[0] = {'\0'};
Tom.id = 0;

/* 用memset()清空结构体 */
memset(&Tom, 0, sizeof(Tom));
// 注意&

如果是结构体数组：

struct Student students[10];
memset(students, 0, sizeof(students) * 10);
1
2
PS：【需要再研究下，结构体对齐问题，比如name[17]时；“如果结构体中有数组的话还是需要对数组单独进行初始化处理的。”啥意思】

二、fill()
C++专用

1.头文件
#include <iostream>
using namespace std;
2.函数原型
作用：将val赋给范围内的所有元素[first, last]。

fill 的前两个参数是定义序列的正向迭代器，第三个参数是赋给每个元素的值。

只要在类型表示的范围内，val随便赋值。

template <class ForwardIterator, class T>
  void fill (ForwardIterator first, ForwardIterator last, const T& val)
{
  while (first != last) {
    *first = val;
    ++first;
  }
}

【解析：first和last其实也是获得地址的位置，但是有限制】
它是用*first来获得值修改的，所以只能套一层，*p直接就是值，不能**p才获得值。

3.例子
（1）数组
int a[5];

fill(a, a + 5, 0);
fill(&a[0], a + 5, 0);
fill(&a[0], &a[5], 1);		// 因为是"不到last"
fill(&a[0], a + sizeof(a) / sizeof(int), 1);
fill(&a[0], a + sizeof(a) / sizeof(a[0]), 1);
int a[5][5];

// fill(a, a + 5 * 5, 0);			// 报错，'const int' to 'int [5]'
// fill(&a, &a + 5 * 5, 0);			// 报错，'const int' to 'int [5][5]'
// fill(&a[0], &a[0] + 5 * 5, 0);	// 报错，'const int' to 'int [5]'
fill(a[0], a[0] + 5 * 5, 0);
fill(&a[0][0], &a[5][5], 0);
fill(&a[0][0], &a[0][0] + 5 * 5, 0);
fill(&a[0][0], &a[0][0] + sizeof(a) / sizeof(int), 0);

三、总结
1.都可以挑选位置设置
并不局限于只是全部的元素

int a[5] = {};

memset(&a[1], -1, sizeof(int) * 2);
// memset(&a[1], -1, (&a[3] - &a[1]) * sizeof(a[0]));

// fill(&a[1], &a[3], -1);

for (int i = 0; i < 5; i++)
{
    cout << a[i] << " ";
}

int a[5][5] = {};

memset(&a[1][2], -1, (&a[3][4] - &a[1][2]) * sizeof(a[0][0]));

// fill(&a[1][2], &a[3][4], 0);

for (int i = 0; i < 5; i++)
{
    for (int j = 0; j < 5; j++)
    {
        cout << a[i][j] << " ";
    }
    cout << endl;
}
cout << endl;

2.sizeof()的陷阱
就是获取所占空间大小的字节数（= 单个元素类型的字节数×数组元素个数），但注意数组传参的陷阱。

（win64下）数组传参进来是一个指针，而指针的类型是8个字节。而不是应该的5x4=20

void fun(int a[5])
{
	cout << sizeof(a) << endl;
	// 8
}
————————————————
版权声明：本文为CSDN博主「sandalphon4869」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/sandalphon4869/article/details/105404397

 

题目：

hdu_2017

　　isdigit(c);  //若是数字，返回true

hdu_1062

getline(cin,a);  //读入一行到a

a.find(" ");  //在a中找" ",也可找字符串或者字符，若找不到返回a.npos(4294967295)

a.substr(i,j);  //截取a中从i到j的子串（包括i不包括j）

a.substr(i);  //截取a中从i到末尾的子串

reverse(a.begin(),a.end());  //反转a

 

hdu_1113

　　string a;

　　sort(a.begin(),a.end());  //sort可以给string排序



