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
