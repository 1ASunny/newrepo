# STL

C++ 标准模板库的核心包括以下三个组件：

| 组件                | 描述                                                         |
| :------------------ | :----------------------------------------------------------- |
| 容器（Containers）  | 容器是用来管理某一类对象的集合。C++ 提供了各种不同类型的容器，比如 deque、list、vector、map 等。 |
| 算法（Algorithms）  | 算法作用于容器。它们提供了执行各种操作的方式，包括对容器内容执行初始化、排序、搜索和转换等操作。 |
| 迭代器（iterators） | 迭代器用于遍历对象集合的元素。这些集合可能是容器，也可能是容器的子集。 |

## 容器（Containers）

### String

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

### Vector

相当于二维数组

#### 基本函数

`vector<int>a;`

1.构造函数
vector():创建一个空vector

vector(int nSize):创建一个vector,元素个数为nSize

vector(int nSize,const t& t):创建一个vector，元素个数为nSize,且值均为t

vector(const vector&):复制构造函数

vector(begin,end):复制[begin,end)区间内另一个数组的元素到vector中
2.增加函数
void push_back(const T& x):向量尾部增加一个元素X，

​		`a.push_back(5)` 在数组的最后添加一个数据
iterator insert(iterator it,const T& x):向量中迭代器指向元素前增加一个元素x

iterator insert(iterator it,int n,const T& x):向量中迭代器指向元素前增加n个相同的元素x

iterator insert(iterator it,const_iterator first,const_iterator last):向量中迭代器指向元素前插入另一个相同类型向量的[first,last)间的数据

`a.insert(a.begin()+i,b)`在第i+1个元素前面插入b;

3.删除函数
iterator erase(iterator it):删除向量中迭代器指向元素
iterator erase(iterator first,iterator last):删除向量中[first,last)中元素
void pop_back():删除向量中最后一个元素
void clear():清空向量中所有元素

em:

`a.erase(a.begin()+2)` ; 删除第3个元素

`a.erase(a.begin()+i,a.end()+j)`; 删除区间[ i,j-1] 区间从0开始



4.遍历函数
reference at(int pos):返回pos位置元素的引用
reference front():返回首元素的引用
reference back():返回尾元素的引用
iterator begin():返回向量头指针，指向第一个元素
iterator end():返回向量尾指针，指向向量最后一个元素的下一个位置
reverse_iterator rbegin():反向迭代器，指向最后一个元素

`a.rbegin()`

> 何种类型的迭代器，说明该类型可以使用该迭代器的函数进行操作

reverse_iterator rend():反向迭代器，指向第一个元素之前的位置
5.判断函数
bool empty() const:判断向量是否为空，若为空，则向量中无元素
6.大小函数
int size() const:返回向量中元素的个数
int capacity() const:返回当前向量所能容纳的最大元素值
int max_size() const:返回最大可允许的 vector 元素数量值
7.其他函数
void swap(vector&):交换两个同类型向量的数据
void assign(int n,const T& x):设置向量中前n个元素的值为x
void assign(const_iterator first,const_iterator last):向量中[first,last)中元素设置成当前向量元素

8.other

1.。。

2.pop_back 去掉数组的最后一个数据

3.at 得到编号位置的数据

4.begin 得到数组头的指针

5.end 得到数组的最后一个单元+1的指针

6.front 得到数组头的引用

7.back 得到数组的最后一个单元的引用

8.max_size 得到vector最大可以是多大

9.capacity 当前vector分配的大小

10.size 当前使用数据的大小

11.resize 改变当前使用数据的大小，如果它比当前使用的大，者填充默认值

12.reserve 改变当前vecotr所分配空间的大小

13.erase 删除指针指向的数据项

14.clear 清空当前的vector

15.rbegin 将vector反转后的开始指针返回(其实就是原来的end-1)

16.rend 将vector反转构的结束指针返回(其实就是原来的begin-1)

17.empty 判断vector是否为空

18.swap 与另一个vector交换数据

#### 用法

Vector<类型>标识符
Vector<类型>标识符(最大容量)
Vector<类型>标识符(最大容量,初始所有值)
Int i[5]={1,2,3,4,5}Vector<类型>vi(I,i+2);//得到i索引值为3以后的值
Vector< vector< int> >v; 二维向量//这里最外的<>要有空格。否则在比较旧的编译器下无法通过

**使用vector注意事项：**

1、如果你要表示的向量长度较长（需要为向量内部保存很多数），容易导致内存泄漏，而且效率会很低；

2、Vector 作为函数的参数或者返回值时，需要注意它的写法：

```
double Distance(vector<int>&a, vector<int>&b)
```

 其中的“&”绝对不能少！！！

em:

		vector<vector<Point2f> > points; //定义一个二维数组

points[0].size();  //指第一行的列数

记住下标是从0开始的。

(5)使用迭代器访问元素.

```c++
vector<int>::iterator it;
for(it=vec.begin();it!=vec.end();it++)
    cout<<*it<<endl;
```

### #迭代器iterator

**迭代器(iterator)**

**是一种检查容器内元素并遍历元素的数据类型。**

(1) 每种容器类型都定义了自己的迭代器类型，如vector:
`vector<int>::iterator iter;`这条语句定义了一个名为iter的变量，它的数据类型是由`vector<int>`定义的iterator类型。
(2) 使用迭代器读取vector中的每一个元素：
`vector<int> p(10,1);`
`for(vector<int>::iterator iter=p.begin();iter!=p.end();++p)
{
*iter=2; //使用 * 访问迭代器所指向的元素
}`
**const_iterator:**
只能读取容器中的元素，而不能修改。
`for(vector<int>::const_iterator citer=ivec.begin();citer!=ivec.end();citer++)
{
cout<<*citer;
//*citer=3; error
}`
vector<int>::const_iterator 和 const vector<int>::iterator的区别:

​		`const vector<int>::iterator newiter=p.begin();`
​		`newiter=11; //可以修改指向容器的元素
​		//newiter++; //迭代器本身不能被修改`
(3) iterator的算术操作：
iterator除了进行++,--操作，可以将iter+n,iter-n赋给一个新的iteraor对象。还可以使用一个iterator减去另外一个iterator.
`const vector<int>::iterator newiter=p.begin();
vector<int>::iterator newiter2=p.end();
cout<<"\n"<<newiter2-newiter;`

#### 详解（搬运）（STL迭代器）iterator详解



要访问顺序容器和关联容器中的元素，需要通过“迭代器（iterator）”进行。迭代器是一个变量，相当于容器和操纵容器的算法之间的中介。迭代器可以指向容器中的某个元素，通过迭代器就可以读写它指向的元素。从这一点上看，迭代器和[指针](http://c.biancheng.net/c/80/)类似。

迭代器按照定义方式分成以下四种。

\1) 正向迭代器，定义方法如下：

容器类名::iterator 迭代器名;


\2) 常量正向迭代器，定义方法如下：

容器类名::const_iterator 迭代器名;


\3) 反向迭代器，定义方法如下：

容器类名::reverse_iterator 迭代器名;


\4) 常量反向迭代器，定义方法如下：

容器类名::const_reverse_iterator 迭代器名;

##### 迭代器用法示例

通过迭代器可以读取它指向的元素，~*迭代器名~就表示迭代器指向的元素。通过非常量迭代器还能修改其指向的元素。

迭代器都可以进行`++`操作。反向迭代器和正向迭代器的区别在于：

- 对正向迭代器进行`++`操作时，迭代器会指向容器中的后一个元素；
- 而对反向迭代器进行`++`操作时，迭代器会指向容器中的前一个元素。


下面的程序演示了如何通过迭代器遍历一个 vector 容器中的所有元素。

```c++
#include <iostream>
#include <vector>
using namespace std;
int main(){  
    vector<int> v;  //v是存放int类型变量的可变长数组，开始时没有元素 
    for (int n = 0; n<5; ++n)        
        v.push_back(n); 
    //push_back成员函数在vector容器尾部添加一个元素 
    vector<int>::iterator i;  //定义正向迭代器  
    for (i = v.begin(); i != v.end(); ++i) {  //用迭代器遍历容器  
        cout << *i << " ";  //*i 就是迭代器i指向的元素      
        *i *= 2;  //每个元素变为原来的2倍  
    }  
        cout << endl;    //用反向迭代器遍历容器  
    for (vector<int>::reverse_iterator j = v.rbegin(); j != v.rend(); ++j)    
        cout << *j << " ";   
    return 0;}
```

程序的输出结果是：
0 1 2 3 4
8 6 4 2 0

第 6 行，vector 容器有多个构造函数，如果用无参构造函数初始化，则容器一开始是空的。

第 10 行，begin 成员函数返回指向容器中第一个元素的迭代器。++i 使得 i 指向容器中的下一个元素。end 成员函数返回的不是指向最后一个元素的迭代器，而是指向最后一个元素后面的位置的迭代器，因此循环的终止条件是`i != v.end()`。

第 16 行定义了反向迭代器用以遍历容器。反向迭代器进行`++`操作后，会指向容器中的上一个元素。rbegin 成员函数返回指向容器中最后一个元素的迭代器，rend 成员函数返回指向容器中第一个元素前面的位置的迭代器，因此本循环实际上是从后往前遍历整个数组。

如果迭代器指向了容器中最后一个元素的后面或第一个元素的前面，再通过该迭代器访问元素，就有可能导致程序崩溃，这和访问 NULL 或未初始化的指针指向的地方类似。

第 10 行和第 16 行，写`++i`、`++j`相比于写`i++`、`j++`，程序的执行速度更快。回顾`++`被重载成前置和后置运算符的例子如下：

```c++
CDemo CDemo::operator++ (){
    //前置++
    ++n;    return *this;}
CDemo CDemo::operator ++(int k){
    //后置++   
    CDemo tmp(*this); 
    //记录修改前的对象   
    n++;    return tmp;  
    //返回修改前的对象}
```

后置`++`要多生成一个局部对象 tmp，因此执行速度比前置的慢。同理，迭代器是一个对象，[STL](http://c.biancheng.net/stl/) 在重载迭代器的`++`运算符时，后置形式也比前置形式慢。在次数很多的循环中，`++i`和`i++`可能就会造成运行时间上可观的差别了。因此，本教程在前面特别提到，对循环控制变量i，要养成写`++i`、不写`i++`的习惯。

注意，容器适配器 stack、queue 和 priority_queue 没有迭代器。容器适配器有一些成员函数，可以用来对元素进行访问。

##### 迭代器的功能分类

不同容器的迭代器，其功能强弱有所不同。容器的迭代器的功能强弱，决定了该容器是否支持 STL 中的某种算法。例如，排序算法需要通过随机访问迭代器来访问容器中的元素，因此有的容器就不支持排序算法。

常用的迭代器按功能强弱分为输入、输出、正向、双向、随机访问五种，这里只介绍常用的三种。

\1) 正向迭代器。假设 p 是一个正向迭代器，则 p 支持以下操作：++p，p++，*p。此外，两个正向迭代器可以互相赋值，还可以用`==`和`!=`运算符进行比较。

\2) 双向迭代器。双向迭代器具有正向迭代器的全部功能。除此之外，若 p 是一个双向迭代器，则`--p`和`p--`都是有定义的。`--p`使得 p 朝和`++p`相反的方向移动。

\3) 随机访问迭代器。随机访问迭代器具有双向迭代器的全部功能。若 p 是一个随机访问迭代器，i 是一个整型变量或常量，则 p 还支持以下操作：

- p+=i：使得 p 往后移动 i 个元素。
- p-=i：使得 p 往前移动 i 个元素。
- p+i：返回 p 后面第 i 个元素的迭代器。
- p-i：返回 p 前面第 i 个元素的迭代器。
- p[i]：返回 p 后面第 i 个元素的引用。


此外，两个随机访问迭代器 p1、p2 还可以用 <、>、<=、>= 运算符进行比较。`p1<p2`的含义是：p1 经过若干次（至少一次）`++`操作后，就会等于 p2。其他比较方式的含义与此类似。

对于两个随机访问迭代器 p1、p2，表达式`p2-p1`也是有定义的，其返回值是 p2 所指向元素和 p1 所指向元素的序号之差（也可以说是 p2 和 p1 之间的元素个数减一）。

表1所示为不同容器的迭代器的功能。



| 容器           | 迭代器功能   |
| -------------- | ------------ |
| vector         | 随机访问     |
| deque          | 随机访问     |
| list           | 双向         |
| set / multiset | 双向         |
| map / multimap | 双向         |
| stack          | 不支持迭代器 |
| queue          | 不支持迭代器 |
| priority_queue | 不支持迭代器 |


例如，vector 的迭代器是随机迭代器，因此遍历 vector 容器有以下几种做法。下面的程序中，每个循环演示了一种做法。

【实例】遍历 vector 容器。

```c++
#include <iostream>
#include <vector>
using namespace std;int main(){
    vector<int> v(100); //v被初始化成有100个元素 
    for(int i = 0;i < v.size() ; ++i) //size返回元素个数
        cout << v[i]; //像普通数组一样使用vector容器
    vector<int>::iterator i;
    for(i = v.begin(); i != v.end (); ++i) //用 != 比较两个迭代器 
        cout << * i;    for(i = v.begin(); i < v.end ();++i) //用 < 比较两个迭代器
            cout << * i;    i = v.begin(); 
    while(i < v.end()) { 
        //间隔一个输出       
        cout << * i;      
        i += 2; // 随机访问迭代器支持 "+= 整数"  的操作
    }}
```

list 容器的迭代器是双向迭代器。假设 v 和 i 的定义如下：

```
list<int> v;list<int>::const_iterator i;
```

则以下代码是合法的：

```
for(i=v.begin(); i!=v.end(); ++i)cout << *i;
```

以下代码则不合法：

```
for(i=v.begin(); i<v.end(); ++i)cout << *i;
```

因为双向迭代器不支持用“<”进行比较。以下代码也不合法：

```
for(int i=0; i<v.size(); ++i)cout << v[i];
```

因为 list 不支持随机访问迭代器的容器，也不支持用下标随机访问其元素。

在 [C++](http://c.biancheng.net/cplus/) 中，数组也是容器。数组的迭代器就是指针，而且是随机访问迭代器。例如，对于数组 int a[10]，int * 类型的指针就是其迭代器。则 a、a+1、a+2 都是 a 的迭代器。

##### 迭代器的辅助函数

STL 中有用于操作迭代器的三个函数模板，它们是：

- advance(p, n)：使迭代器 p 向前或向后移动 n 个元素。
- dis[tan](http://c.biancheng.net/ref/tan.html)ce(p, q)：计算两个迭代器之间的距离，即迭代器 p 经过多少次 + + 操作后和迭代器 q 相等。如果调用时 p 已经指向 q 的后面，则这个函数会陷入死循环。
- iter_swap(p, q)：用于交换两个迭代器 p、q 指向的值。


要使用上述模板，需要包含头文件 algorithm。下面的程序演示了这三个函数模板的 用法。

```c++
#include <list>#include <iostream>#include <algorithm> //要使用操作迭代器的函数模板，需要包含此文件
using namespace std;
int main(){   
    int a[5] = { 1, 2, 3, 4, 5 };   
    list <int> lst(a, a+5);   
    list <int>::iterator p = lst.begin();   
    advance(p, 2);  //p向后移动两个元素，指向3   
    cout << "1)" << *p << endl;  //输出 
    advance(p, -1);  //p向前移动一个元素，指向2   
    cout << "2)" << *p << endl;  //输出 2)2    
    list<int>::iterator q = lst.end();   
    q--;  //q 指向 5    
    cout << "3)" << distance(p, q) << endl;  //输出 3)3
    iter_swap(p, q); //交换 2 和 5    
    cout << "4)";    
    for (p = lst.begin(); p != lst.end(); ++p)        
        cout << *p << " ";   
    return 0;}
```

程序的输出结果是：
\1) 3
\2) 2
\3) 3
\4) 1 5 3 4 2

#### 优缺点

   正如前面所说，与集合密切相关，限制了 Iterator模式的广泛使用，符合模式“经常出现的特定问题的解决方案”的特质。在一般的底层集合支持类中，我们往往不愿“避轻就重”将集合设计成集合 + Iterator 的形式，而是将遍历的功能直接交由集合完成，以免犯了“过度设计”的诟病，但是，如果我们的集合类确实需要支持多种遍历方式（仅此一点仍不一定需要考虑 Iterator模式，直接交由集合完成往往更方便），或者，为了与系统提供或使用的其它机制，如STL算法，保持一致时，Iterator模式才值得考虑。

### pair

pair是将2个数据组合成一组数据，当需要这样的需求时就可以使用pair，如stl中的map就是将key和value放在一起来保存。另一个应用是，当一个函数需要返回2个数据的时候，可以选择pair。 pair的实现是一个结构体，主要的两个成员变量是first second 因为是使用struct不是class，所以可以直接使用pair的成员变量。

其标准库类型--pair类型定义在#include <utility>头文件中，定义如下：

类模板：template<class T1,class T2> struct pair

参数：T1是第一个值的数据类型，T2是第二个值的数据类型。

功能：pair将一对值(T1和T2)组合成一个值， 这一对值可以具有不同的数据类型（T1和T2），两个值可以分别用pair的两个公有函数first和second访问。

**2，pair的创建和初始化**

pair包含两个数值，与容器一样，pair也是一种模板类型。但是又与之前介绍的容器不同；

在创建pair对象时，必须提供两个类型名，两个对应的类型名的类型不必相同

`pair<string, string> anon;        // 创建一个空对象anon，两个元素类型都是string
pair<string, int> word_count;     // 创建一个空对象 word_count, 两个元素类型分别是string和int类型
pair<string, vector<int> > line;  // 创建一个空对象line，两个元素类型分别是string和vector
`，

pair对象的操作

访问两个元素操作可以通过first和sencond访问：

`pair<int ,double> p1;`

`p1.first = 1;`

`p1.second = 2.5;`

`cout<<p1.first<<' '<<p1.second<<endl;`

//输出结果：1 2.5

`string firstBook;
if(author.first=="James" && author.second=="Joy")
    firstBook="Stephen Hero";`
4，生成新的pair对象

还可以利用make_pair创建新的pair对象：

` pair<int, double> p1;
 p1 = make_pair(1, 1.2);`

`cout << p1.first << p1.second << endl;`

//output: 1 1.2

`int a = 8;`

`string m = "James";`

`pair<int, string> newone;`

`newone = make_pair(a, m);`
`cout << newone.first << newone.second << endl;`

//output: 8 James
5，通过tie获取pair元素值

在某些清况函数会以pair对象作为返回值时，可以直接通过std::tie进行接收。比如：

`std::pair<std::string, int> getPreson() {
    return std::make_pair("Sven", 25);`
}`

`int main(int argc, char **argv) {
    std::string name;
    int ages;`

    std::tie(name, ages) = getPreson();
     
    std::cout << "name: " << name << ", ages: " << ages << std::endl;
     
    return 0;

### Hash

哈希表（Hash table，也叫散列表），是根据关键码值(Key value)而直接进行访问的数据结构。也就是说，它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫做散列函数，存放记录的数组叫做散列表。

记录的存储位置=f(关键字)

这里的对应关系f称为散列函数，又称为哈希（Hash函数），采用散列技术将记录存储在一块连续的存储空间中，这块连续存储空间称为散列表或哈希表（Hash table）。
    而当使用哈希表进行查询的时候，就是再次使用哈希函数将key转换为对应的数组下标，并定位到该空间获取value，如此一来，就可以充分利用到数组的定位性能进行数据定位。

#### 生成哈希值的函数

functional 头文件中定义了无序关联容器使用的特例化 hash<K> 模板。hash<K> 模板定义了可以从 K 类型的对象生成哈希值的函数对象的类型。hash<K> 实例的成员函数 operator()() 接受 K 类型的单个参数，然后返回 size_t 类型的哈希值。对于基本类型和指针类型，也定义了特例化的 hash<K> 模板。

hash<K> 模板专用的算法取决于实现，但是如果它们遵循 [C++](http://c.biancheng.net/cplus/)14 标准的话，需要满足一些具体的要求。这些要求如下：

- 不能拋出异常

- 对于相等的键必须产生相等的哈希值

- 对于不相等的键产生碰撞的可能性必须最小接近 size_t 最大值的倒数

  相等键生成相等的哈希值只适用于单次执行。这也就意味着，在不同的场合允许给定的键可以生成不同的哈希值。这就使我们可以在哈希算法中使用随机数，当对密码进行哈希时，这是我们所希望使用的。注意，C++14 为了保持一致性并没有排除给定类型的键的哈希值等同于键的可能。在无序关联容器中，用哈希函数哈希整数值可能就是这种情况。

```c++
std::hash<int> hash_int;// Function object to hash int
std::vector<int> {-5, -2, 2, 5, 10};
std::transform(std::begin(n), std::end(n),std::ostream_iterator<size_t> (std:: cout," "),hash_int);
```

> 这里使用 transform() 算法来哈希 vector 中的元素。transform() 参数中的前两个迭代器指定了被操作元素的范围，第三个参数是一个指定输出地址的迭代器，这里是一个 ostream 迭代器，最后一个参数是应用到范围元素上的函数对象 hash<int>。某次测试的输出结果为：
>
> 554121069 2388331168 3958272823 3132668352 1833987007

```c++
std::hash<double> hash_double;
std::vector<double> x {3.14,-2.71828, 99.0, 1.61803399,6.62606957E-34};
std::transform(std::begin(x), std::end(x),std::ostream_iterator<size_t>(std::cout," "),hash_double);
//double


std::hash<Box*> hash_box; // Box class as in Chapter 2
Box box{1, 2, 3};
std:: cout << "Hash value = " << hash_box (&box)<<std::endl; // Hash value = 2916986638
//node


std::hash<Box*> hash_box; // Box class as in Chapter 2
auto upbox = std::make_unique<Box>(1A 2, 3);
std::cout << "Hash value = " << hash_box(upbox.get())<<std::endl; // Hash value = 1143026886
//函数对象
```



#### 拉链法

左边很明显是个数组，数组的每个成员包括一个指针，指向一个链表的头，当然这个链表可能为空，也可能元素很多。我们根据元素的一些特征把元素分配到不同的链表中去，也是根据这些特征，找到正确的链表，再从链表中找出这个元素。

我想大家都在想一个很严重的问题：“如果两个字符串在哈希表中对应的位置相同怎么办？”,毕竟一个数组容量是有限的，这种可能性很大。解决该问题的方法很多，我首先想到的就是用“链表”。我遇到的很多算法都可以转化成链表来解决，只要在哈希表的每个入口挂一个链表，保存所有对应的字符串就OK了

散列法：元素特征转变为数组下标的方法。

1，除法散列法 
最直观的一种，上图使用的就是这种散列法，公式： 
      index = value % 16 
学过汇编的都知道，求模数其实是通过一个除法运算得到的，所以叫“除法散列法”。

2，平方散列法 
求index是非常频繁的操作，而乘法的运算要比除法来得省时（对现在的CPU来说，估计我们感觉不出来），所以我们考虑把除法换成乘法和一个位移操作。公式： 
      index = (value * value) >> 28   （右移，除以2^28。记法：左移变大，是乘。右移变小，是除。）
如果数值分配比较均匀的话这种方法能得到不错的结果，但我上面画的那个图的各个元素的值算出来的index都是0——非常失败。也许你还有个问题，value如果很大，value * value不会溢出吗？答案是会的，但我们这个乘法不关心溢出，因为我们根本不是为了获取相乘结果，而是为了获取index。

3，斐波那契（Fibonacci）散列法

平方散列法的缺点是显而易见的，所以我们能不能找出一个理想的乘数，而不是拿value本身当作乘数呢？答案是肯定的。

1，对于16位整数而言，这个乘数是40503 
2，对于32位整数而言，这个乘数是2654435769 
3，对于64位整数而言，这个乘数是11400714819323198485

这几个“理想乘数”是如何得出来的呢？这跟一个法则有关，叫黄金分割法则，而描述黄金分割法则的最经典表达式无疑就是著名的斐波那契数列，即如此形式的序列：0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233,377, 610， 987, 1597, 2584, 4181, 6765, 10946，…。另外，斐波那契数列的值和太阳系八大行星的轨道半径的比例出奇吻合。

对我们常见的32位整数而言，公式： 
        index = (value * 2654435769) >> 28



#### 散列冲突的解决

冲突主要取决于：

　　（1）散列函数，一个好的散列函数的值应尽可能平均分布。

　　（2）处理冲突方法。

　　（3）负载因子的大小。太大不一定就好，而且浪费空间严重，负载因子和散列函数是联动的。

解决冲突的办法：

　　（1）线性探查法：冲突后，线性向前试探，找到最近的一个空位置。缺点是会出现堆积现象。存取时，可能不是同义词的词也位于探查序列，影响效率。

　　（2）双散列函数法：在位置d冲突后，再次使用另一个散列函数产生一个与散列表桶容量m互质的数c，依次试探（d+n*c）%m，使探查序列跳跃式分布。


1.建立一个缓冲区，把凡是拼音重复的人放到缓冲区中。当我通过名字查找人时，发现找的不对，就在缓冲区里找。

2.进行再探测。就是在其他地方查找。探测的方法也可以有很多种。

（1）在找到查找位置的index的index-1，index+1位置查找，index-2，index+2查找，依次类推。这种方法称为线性再探测。

（2）在查找位置index周围随机的查找。称为随机在探测。

（3）再哈希。就是当冲突时，采用另外一种映射方式来查找。

这个程序中是通过取模来模拟查找到重复元素的过程。对待重复元素的方法就是再哈希：对当前key的位置+7。最后，可以通过全局变量来判断需要查找多少次。我这里通过依次查找26个英文字母的小写计算的出了总的查找次数。显然，当总的查找次数/查找的总元素数越接近1时，哈希表更接近于一一映射的函数，查找的效率更高。

#### 常用的构造散列函数的方法

　　散列函数能使对一个数据序列的访问过程更加迅速有效，通过散列函数，数据元素将被更快地定位：

  1. 直接寻址法：取关键字或关键字的某个线性函数值为散列地址。即H（key）=key或H（key） = a？key + b，其中a和b为常数（这种散列函数叫做自身函数）

  2. 数字分析法：分析一组数据，比如一组员工的出生年月日，这时我们发现出生年月日的前几位数字大体相同，这样的话，出现冲突的几率就会很大，但是我们发现年月日的后几位表示月份和具体日期的数字差别很大，如果用后面的数字来构成散列地址，则冲突的几率会明显降低。因此数字分析法就是找出数字的规律，尽可能利用这些数据来构造冲突几率较低的散列地址。

  3. 平方取中法：取关键字平方后的中间几位作为散列地址。

  4. 折叠法：将关键字分割成位数相同的几部分，最后一部分位数可以不同，然后取这几部分的叠加和（去除进位）作为散列地址。

  5. 随机数法：选择一随机函数，取关键字的随机值作为散列地址，通常用于关键字长度不同的场合。

  6. 除留余数法：取关键字被某个不大于散列表表长m的数p除后所得的余数为散列地址。即 H（key） = key MOD p， p《=m。不仅可以对关键字直接取模，也可在折叠、平方取中等运算之后取模。对p的选择很重要，一般取素数或m，若p选的不好，容易产生同义词。

  

#### hash_map





### map

作为关联式容器的一种，map 容器存储的都是 pair 对象，也就是用 pair 类模板创建的键值对。其中，各个键值对的键和值可以是任意数据类型，包括 C++ 基本数据类型（int、double 等）、使用结构体或类自定义的类型。

通常情况下，map 容器中存储的各个键值对都选用 string 字符串作为键的类型。

它提供一对一（其中第一个可以称为关键字，每个关键字只能在map中出现一次，第二个可能称为该关键字的值）的数据处理能力，由于这个特性，它完成有可能在我们处理一对一数据的时候，在编程上提供快速通道。这里说下map内部数据的组织，map内部自建一颗红黑树(一 种非严格意义上的平衡二叉树)，这颗树具有对数据自动排序的功能，所以在map内部所有的数据都是有序的，后边我们会见识到有序的好处。

需要注意的是，使用 map 容器存储的各个键值对，键的值既不能重复也不能被修改。换句话说，**map 容器中存储的各个键值对不仅键的值独一无二，键的类型也会用 const 修饰，**这意味着只要键值对被存储到 map 容器中，其键的值将不能再做任何修改。如果出现重复的key，后出现的不会覆盖前出现的，而是会以前出现的为准。对于迭代器来说，可以修改实值，而不能修改key。

该容器存储的都是 pair<const K, T> 类型（其中 K 和 T 分别表示键和值的数据类型）的键值对元素。

```c++
template < class Key,                                     // 指定键（key）的类型
           class T,                                       // 指定值（value）的类型
           class Compare = less<Key>,                     // 指定排序规则
           class Alloc = allocator<pair<const Key,T> >    // 指定分配器对象的类型
           > class map;
```

map 容器模板有 4 个参数，其中后 2 个参数都设有默认值。大多数场景中，我们只需要设定前 2 个参数的值，有些场景可能会用到第 3 个参数，但最后一个参数几乎不会用到。

1) 通过调用 map 容器类的默认构造函数，可以创建出一个空的 map 容器，比如：

```c++
std::map<std::string, int>myMap;
```

2) 当然在创建 map 容器的同时，也可以进行初始化，比如：

```c++
std::map<std::string, int>myMap{ {"C语言教程",10},{"STL教程",20} };
```

3) 除此之外，在某些场景中，可以利用先前已创建好的 map 容器，再创建一个新的 map 容器。例如：

```c++
std::map<std::string, int>newMap(myMap);
```

由此，通过调用 map 容器的拷贝（复制）构造函数，即可成功创建一个和 myMap 完全一样的 newMap 容器。

C++ 11 标准中，还为 map 容器增添了移动构造函数。当有临时的 map 对象作为参数，传递给要初始化的 map 容器时，此时就会调用移动构造函数。举个例子：

```c++
#创建一个会返回临时 map 对象的函数
std::map<std::string,int> disMap() {   std::map<std::string, int>tempMap{ {"C语言教程",10},{"STL教程",20} };    return tempMap;}//调用 map 类模板的移动构造函数创建 newMap 容器std::map<std::string, int>newMap(disMap());
```

> 注意，无论是调用复制构造函数还是调用拷贝构造函数，都必须保证这 2 个容器的类型完全一致。

4) map 类模板还支持取已建 map 容器中指定区域内的键值对，创建并初始化新的 map 容器。例如：

```c++
std::map<std::string, int>myMap{ {"C语言教程",10},{"STL教程",20} };
std::map<std::string, int>newMap(++myMap.begin(), myMap.end());
```

这里，通过调用 map 容器的双向迭代器，实现了在创建 newMap 容器的同时，将其初始化为包含一个 {"STL教程",20} 键值对的容器。

5) 当然，在以上几种创建 map 容器的基础上，我们都可以手动修改 map 容器的排序规则。默认情况下，map 容器调用 std::less<T> 规则，根据容器内各键值对的键的大小，对所有键值对做升序排序。

因此，如下 2 行创建 map 容器的方式，其实是等价的：

```c++
std::map<std::string, int>myMap{ {"C语言教程",10},{"STL教程",20} };std::map<std::string, int, std::less<std::string> >myMap{ {"C语言教程",10},{"STL教程",20} };
```

以上 2 中创建方式生成的 myMap 容器，其内部键值对排列的顺序为：

<"C语言教程", 10>
<"STL教程", 20>
下面程序手动修改了 myMap 容器的排序规则，令其作降序排序：

```c++
std::map<std::string, int, std::greater<std::string> >myMap{ {"C语言教程",10},{"STL教程",20} };
```

此时，myMap 容器内部键值对排列的顺序为：

<"STL教程", 20>
<"C语言教程", 10>

> 在某些特定场景中，我们还需要为 map 容器自定义排序规则，此部分知识后续将利用整整一节做重点讲解。

#### 常用方法

| 成员方法         | 功能                                                         |
| ---------------- | :----------------------------------------------------------- |
| **begin()**      | 返回指向容器中第一个（注意，是已排好序的第一个）键值对的双向迭代器。如果 map 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。 |
| **end()**        | 返回指向容器最后一个元素（注意，是已排好序的最后一个）所在位置后一个位置的双向迭代器，通常和 begin() 结合使用。如果 map 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。 |
| rbegin()         | 返回指向最后一个（注意，是已排好序的最后一个）元素的反向双向迭代器。如果 map 容器用 const 限定，则该方法返回的是 const 类型的反向双向迭代器。 |
| rend()           | 返回指向第一个（注意，是已排好序的第一个）元素所在位置前一个位置的反向双向迭代器。如果 map 容器用 const 限定，则该方法返回的是 const 类型的反向双向迭代器。 |
| cbegin()         | 和 begin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。 |
| cend()           | 和 end() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。 |
| crbegin()        | 和 rbegin() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。 |
| crend()          | 和 rend() 功能相同，只不过在其基础上，增加了 const 属性，不能用于修改容器内存储的键值对。 |
| **find(key)**    | 在 map 容器中查找键为 key 的键值对，如果成功找到，则返回指向该键值对的双向迭代器；反之，则返回和 end() 方法一样的迭代器。另外，如果 map 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。**map的底层实现是红黑树，map是有序的，增删查改一个元素的时间复杂度都是O(log n),使用迭代器遍历map的时间复杂度是O(n)**                                                          注意，在使用[]运算符返回map中的一个键对应的值时，需要先判断值该键值对是否存在。当使用[]时即使查找的键不存在编译器也不会报错，而是返回垃圾值。                                                `if(a.count(2) > 0) // 方法一                 return a[2];                          auto iter1 = a.find(2);// 方法二       if(iter != end(a))                  return iter->second;`                                       通常可以使用count和find方法判断一个键是否存在，由于map内部时有序的所以不需要遍历全部键值对。count返回个数，find返回找到的元素的位置，如果找不到返回map的末尾位置。以下展示了两种方法寻找键值对，第二种方法更好，因为第一种方法找了两遍。[]运算符可以使用at成员函数代替。 |
| lower_bound(key) | 返回一个指向当前 map 容器中第一个大于或等于 key 的键值对的双向迭代器。如果 map 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。 |
| upper_bound(key) | 返回一个指向当前 map 容器中第一个大于 key 的键值对的迭代器。如果 map 容器用 const 限定，则该方法返回的是 const 类型的双向迭代器。 |
| equal_range(key) | 该方法返回一个 pair 对象（包含 2 个双向迭代器），其中 pair.first 和 lower_bound() 方法的返回值等价，pair.second 和 upper_bound() 方法的返回值等价。也就是说，该方法将返回一个范围，该范围中包含的键为 key 的键值对（map 容器键值对唯一，因此该范围最多包含一个键值对）。 |
| **empty() **     | 若容器为空，则返回 true；否则 false。                        |
| **size()**       | 返回当前 map 容器中存有键值对的个数。                        |
| max_size()       | 返回 map 容器所能容纳键值对的最大个数，不同的操作系统，其返回值亦不相同。 |
| operator[]       | map容器重载了 [] 运算符，只要知道 map 容器中某个键值对的键的值，就可以向获取数组中元素那样，通过键直接获取对应的值。 |
| **at(key)**      | 找到 map 容器中 key 键对应的值，如果找不到，该函数会引发 out_of_range 异常。 |
| **insert()**     | 向 map 容器中插入键值对。                                  1 a.insert(pair<int, string>(1,"aaa"));                      2 a.insert(make_pair<int, string>(2,"bbb"));           3 a.insert(map<int,string>::value_type(3,"ccc"));                                 4 a[4] = "ddd";                                                         5  map<int, string> mapStudent;            mapStudent[1] = "student_one";     //数组插入                                    前三者是等价的，利用前三种方法插入一个键值对，如果插入的键已存在，编译器会报错，而第四种写法会直接覆盖原先的键值对。 |
| **erase()**      | 删除 map 容器指定位置、指定键（key）值或者指定区域内的键值对。后续章节还会对该方法做重点讲解。 |
| **swap()**       | 交换 2 个 map 容器中存储的键值对，这意味着，操作的 2 个键值对的类型必须相同。 |
| **clear()**      | 清空 map 容器中所有的键值对，即使 map 容器的 size() 为 0。   |
| emplace()        | 在当前 map 容器中的指定位置处构造新键值对。其效果和插入键值对一样，但效率更高。 |
| emplace_hint()   | 在本质上和 emplace() 在 map 容器中构造新键值对的方式是一样的，不同之处在于，使用者必须为该方法提供一个指示键值对生成位置的迭代器，并作为该方法的第一个参数。 |
| **count(key)**   | 在当前 map 容器中，查找键为 key 的键值对的个数并返回。注意，由于 map 容器中各键值对的键的值是唯一的，因此该函数的返回值最大为 1。 |

##### 插入

第一种：用insert函数插入pair数据，下面举例说明(以下代码虽然是随手写的，应该可以在VC和GCC下编译通过，大家可以运行下看什么效果，在VC下请加入这条语句，屏蔽4786警告 ＃pragma warning (disable:4786) )

```javascript
//数据的插入--第一种：用insert函数插入pair数据  
int main()  
{  
    map<int, string> mapStudent;  
    mapStudent.insert(pair<int, string>(1, "student_one")); 
    mapStudent.insert(pair<int, string>(2, "student_two")); 
    mapStudent.insert(pair<int, string>(3, "student_three"));  
    map<int, string>::iterator iter;  
    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)  
       cout<<iter->first<<' '<<iter->second<<endl;  
}  
```

第二种：用insert函数插入value_type数据，下面举例说明

```javascript
//第二种：用insert函数插入value_type数据，下面举例说明  
int main()  
{  
    map<int, string> mapStudent;  
    mapStudent.insert(map<int, string>::value_type (1, "student_one"));  
    mapStudent.insert(map<int, string>::value_type (2, "student_two"));  
    mapStudent.insert(map<int, string>::value_type (3, "student_three"));  
    map<int, string>::iterator iter;  
    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)  
       cout<<iter->first<<' '<<iter->second<<endl;  
}  
```

第三种：用数组方式插入数据，下面举例说明

```c++
//第三种：用数组方式插入数据，下面举例说明  
 
{  
    map<int, string> mapStudent;  
    mapStudent[1] = "student_one";  
    mapStudent[2] = "student_two";  
    mapStudent[3] = "student_three";  
    map<int, string>::iterator iter;  
    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)  
        cout<<iter->first<<' '<<iter->second<<endl;  

}  
```

以上三种用法，虽然都可以实现数据的插入，但是它们是有区别的，当然了第一种和第二种在效果上是完成一样的，用insert函数插入数据，在数据的 插入上涉及到集合的唯一性这个概念，即当map中有这个关键字时，insert操作是插入数据不了的，但是用数组方式就不同了，它可以覆盖以前该关键字对 应的值，用程序说明

```javascript
mapStudent.insert(map<int, string>::value_type (1, "student_one"));

mapStudent.insert(map<int, string>::value_type (1, "student_two"));
```

上面这两条语句执行后，map中1这个关键字对应的值是“student_one”，第二条语句并没有生效，那么这就涉及到我们怎么知道insert语句是否插入成功的问题了，可以用pair来获得是否插入成功，程序如下

```javascript
pair<map<int, string>::iterator, bool> Insert_Pair;

Insert_Pair = mapStudent.insert(map<int, string>::value_type (1, "student_one"));
```

我们通过pair的第二个变量来知道是否插入成功，它的第一个变量返回的是一个map的迭代器，如果插入成功的话Insert_Pair.second应该是true的，否则为false。

下面给出完成代码，演示插入成功与否问题

```javascript
//验证插入函数的作用效果  
int main()  
{  
    map<int, string> mapStudent;  
    pair<map<int, string>::iterator, bool> Insert_Pair;  
    Insert_Pair = mapStudent.insert(pair<int, string>(1, "student_one"));  
    if(Insert_Pair.second == true)  
        cout<<"Insert Successfully"<<endl;  
    else  
        cout<<"Insert Failure"<<endl;  
    Insert_Pair = mapStudent.insert(pair<int, string>(1, "student_two"));  
    if(Insert_Pair.second == true)  
  cout<<"Insert Successfully"<<endl;  
    else  
        cout<<"Insert Failure"<<endl;  
    map<int, string>::iterator iter;  
    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)  
       cout<<iter->first<<' '<<iter->second<<endl;  
}  
```

 大家可以用如下程序，看下用数组插入在数据覆盖上的效果

```c++
//验证数组形式插入数据的效果  

int main()  
{  
    map<int, string> mapStudent;  

    mapStudent[1] = "student_one";  

    mapStudent[1] = "student_two";  

    mapStudent[2] = "student_three";  

    map<int, string>::iterator iter;  

    for(iter = mapStudent.begin(); iter != mapStudent.end(); iter++)  
       cout<<iter->first<<' '<<iter->second<<endl;  

}  
```

##### 查找并获取map中的元素（包括判定这个关键字是否在map中出现）

在这里我们将体会，map在数据插入时保证有序的好处。

要判定一个数据（关键字）是否在map中出现的方法比较多，这里标题虽然是数据的查找，在这里将穿插着大量的map基本用法。

这里给出三种数据查找方法

第一种：用count函数来判定关键字是否出现，其缺点是无法定位数据出现位置,由于map的特性，一对一的映射关系，就决定了count函数的返回值只有两个，要么是0，要么是1，出现的情况，当然是返回1了

第二种：用find函数来定位数据出现位置，它返回的一个迭代器，当数据出现时，它返回数据所在位置的迭代器，如果map中没有要查找的数据，它返回的迭代器等于end函数返回的迭代器。

查找map中是否包含某个关键字条目用find()方法，传入的参数是要查找的key，在这里需要提到的是begin()和end()两个成员，

分别代表map对象中第一个条目和最后一个条目，这两个数据的类型是iterator.

```c++
map<int, string> mapStudent;  

    mapStudent.insert(pair<int, string>(1, "student_one")); 
    mapStudent.insert(pair<int, string>(2, "student_two")); 
    mapStudent.insert(pair<int, string>(3, "student_three"));  
    map<int, string>::iterator iter;  
    iter = mapStudent.find(1);  
    if(iter != mapStudent.end())  
       cout<<"Find, the value is "<<iter->second<<endl;  
    else  
       cout<<"Do not Find"<<endl;  

```

#####  **从map中删除元素**

移除某个map中某个条目用erase（）

该成员方法的定义如下：

iterator erase（iterator it);//通过一个条目对象删除

iterator erase（iterator first，iterator last）//删除一个范围

size_type erase(const Key&key);//通过关键字删除

clear()就相当于enumMap.erase(enumMap.begin(),enumMap.end());

##### **排序 ·  map中的sort问题**

map中的元素是自动按Key升序排序，所以不能对map用sort函数；

这里要讲的是一点比较高深的用法了,排序问题，STL中默认是采用小于号来排序的，以上代码在排序上是不存在任何问题的，因为上面的关键字是int 型，它本身支持小于号运算，在一些特殊情况，比如关键字是一个结构体，涉及到排序就会出现问题，因为它没有小于号操作，insert等函数在编译的时候过不去，下面给出两个方法解决这个问题。

第一种：小于号重载，程序举例。

```c++
typedef struct tagStudentinfo  
{ 
       int      niD; 
       string   strName; 
       bool operator < (tagStudentinfo const& _A) const  
       {     //这个函数指定排序策略，按niD排序，如果niD相等的话，按strName排序  
            if(niD < _A.niD) return true;  
			if(niD == _A.niD)  
            return strName.compare(_A.strName) < 0;  
       		 return false;  
       }  
}Studentinfo, *PStudentinfo; //学生信息  
int main()  
{  
    int nSize;   //用学生信息映射分数  
    map<Studentinfo, int>mapStudent;  
    map<Studentinfo, int>::iterator iter;  
    Studentinfo studentinfo;  
    studentinfo.niD = 1;  
    studentinfo.strName = "student_one";  
    mapStudent.insert(pair<Studentinfo, int>(studentinfo, 90));  
    studentinfo.niD = 2;  
    studentinfo.strName = "student_two";  
    mapStudent.insert(pair<Studentinfo, int>(studentinfo, 80)); 
    for (iter=mapStudent.begin(); iter!=mapStudent.end(); iter++)  
 cout<<iter->first.niD<<' '<<iter->first.strName<<' '<<iter->second<<endl;  
    return 0;  
}
```



第二种：仿函数的应用，这个时候结构体中没有直接的小于号重载，程序说明

```c++
//第二种：仿函数的应用，这个时候结构体中没有直接的小于号重载，程序说明 
typedef struct tagStudentinfo  
{  
       int      niD;  
       string   strName;  
}Studentinfo, *PStudentinfo; //学生信息  
class sort  
{  
public:  
    bool operator() (Studentinfo const &_A, Studentinfo const &_B) const  
    {  
        if(_A.niD < _B.niD)  
            return true;  
        if(_A.niD == _B.niD)  
      return _A.strName.compare(_B.strName) < 0; 
    return false;  
    }  
};  
int main()  

{   //用学生信息映射分数  

    map<Studentinfo, int, sort>mapStudent;  

    map<Studentinfo, int>::iterator iter;  

    Studentinfo studentinfo;  

    studentinfo.niD = 1;  

    studentinfo.strName = "student_one";  

    mapStudent.insert(pair<Studentinfo, int>(studentinfo, 90));  
    studentinfo.niD = 2;  
    studentinfo.strName = "student_two";  
   mapStudent.insert(pair<Studentinfo, int>(studentinfo, 80));  
    for (iter=mapStudent.begin(); iter!=mapStudent.end(); iter++)  
        cout<<iter->first.niD<<' '<<iter->first.strName<<' '<<iter->second<<endl;  

}  
```

##### 遍历

前向

后向

```c++
mapStudent.insert(pair<int, string>(3, "student_three"));  
    map<int, string>::reverse_iterator iter;  
    for(iter = mapStudent.rbegin(); iter != 			       mapStudent.rend(); iter++)  
    cout<<iter->first<<"  "<<iter->second<<endl;  

```

数组

```c++
int nSize = mapStudent.size();  
//此处应注意，应该是 for(int nindex = 1; nindex <= nSize; nindex++)  
//而不是 for(int nindex = 0; nindex < nSize; nindex++)  
    for(int nindex = 1; nindex <= nSize; nindex++)  
        cout<<mapStudent[nindex]<<endl;  
```



#### multimap

multimap 与 map 一样，都是使用红黑树对记录型的元素数据,按元素键值的比较关系，进行快速的插入、删除和检索操作。
所不同的是 multimap 允许将具有重复键值的元素插入容器。在 multimap 容器中，元素的键值与元素的映照数据的映照关系，是多对多的，因此，multimap 称为多重映照容器。
multimap 与 map 之间的多重特性差异，类似于 multiset 与 set 的多重特性差异。
multimap 多重映照容器实现了 Sorted Associative Container 、Pair Associative Container 和 Multimap Associative Container 概念的接口规范。
一些说明：multimap多重映照容器的基础说明：

 * multimap多重映照容器:容器的数据结构采用红黑树进行管理

 * multimap的所有元素都是pair:第一元素为键值(key),不能修改;第二元素为实值(value),可被修改

 * multimap特性以及用法与map完全相同，唯一的差别在于:

 * 允许重复键值的元素插入容器(使用了RB-Tree的insert_equal函数)

    因此

 * 键值key与元素value的映照关系是多对多的关系

 * 没有定义[]操作运算 

 * Sorted Associative Container  Pair Associative Container   Unique Associative Container

 * 使用multimap必须使用宏语句#include <map>


```c++
#include <map>
#include <string>
#include <iostream>
 
// 基本操作与set类型,牢记map中所有元素都是pair
// 对于自定义类,初学者会觉得比较函数如何构造很麻烦,这个可以参照前面的书写示例
// 但若设置键值为int或char类型，无须构造比较函数
 
struct student{
 char* name;
 int age;
 char* city;
 char* phone;
};
 
int main()
{
	 using namespace std;
 
	 student s[]={
	  {"童进",23,"武汉","XXX"},
	  {"老大",23,"武汉","XXX"},
	  {"饺子",23,"武汉","XXX"},
	  {"王老虎",23,"武汉","XXX"},
	  {"周润发",23,"武汉","XXX"},
	  {"周星星",23,"武汉","XXX"}
	 };
	  pair<int,student> p1(4,s[0]);
	  pair<int,student> p2(2,s[1]);
	  pair<int,student> p3(3,s[2]);
	  pair<int,student> p4(4,s[3]);  //键值key与p1相同
	  pair<int,student> p5(5,s[4]);
	  pair<int,student> p6(6,s[5]);
	 multimap<int,student> a;
	 a.insert(p1);
	 a.insert(p2);
	 a.insert(p3);
	 a.insert(p4);
	 a.insert(p5);
	 a.insert(p6);
	 typedef multimap<int,student>::iterator int_multimap;
	 pair<int_multimap,int_multimap> p = a.equal_range(4);
	 int_multimap i = a.find(4);
	 cout<<"班上key值为"<< i->first<<"的学生有："<<a.count(4)<<"名,"<<"   他们是:"<<endl;
	 for(int_multimap k = p.first; k != p.second; k++)
	 {
		cout<<k->second.name<<endl;
	 }
	 cout<<"删除重复键值的同学"<<endl;
	 a.erase(i);
	 cout<<"现在班上总人数为："<<a.size()<<".   人员如下："<<endl;
	 for(multimap<int,student>::iterator j=a.begin(); j != a.end(); j++)
	 {      
		  cout<<"The name: "<<j->second.name<<"      "<<"age: "<<j->second.age<<"   "
		   <<"city: "<<j->second.city<<"      "<<"phone: "<<j->second.phone<<endl;
	 }
 
	 return 0;
}
 
```







































## 算法

#### 排序函数

##### 快排

algorithm库

template <class RandomAccessIterator>
 void sort ( RandomAccessIterator first, RandomAccessIterator last );
template <class RandomAccessIterator, class Compare>
 void sort ( RandomAccessIterator first, RandomAccessIterator last, Compare comp );

第一种：void sort ( RandomAccessIterator first, RandomAccessIterator last );

默认升序

第二种：

bool cmp判断函数

`struct pair1{int a;int b;};
bool cmp(pair1 a,pair1 b){return a.a<b.a;}
int main(){
int t;cin>>t;
while(t--){
pair1 a[N];int n,k;cin>>n>>k;
for(i,1,n) cin>>a[i].a;_for(i,1,n) cin>>a[i].b;sort(a+1,a+1+n,cmp);`