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



