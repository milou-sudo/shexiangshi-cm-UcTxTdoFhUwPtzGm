[合集 \- 3个月搞定计算机二级C语言(5\)](https://github.com)[1\.2个月搞定计算机二级C语言——真题（5）解析10\-29](https://github.com/main-studio/p/18511838)[2\.2个月搞定计算机二级C语言——真题（6）解析10\-30](https://github.com/main-studio/p/18515198)[3\.2个月搞定计算机二级C语言——真题（7）解析11\-03](https://github.com/main-studio/p/18523045)[4\.2个月搞定计算机二级C语言——真题（8）解析11\-03](https://github.com/main-studio/p/18523099)5\.2个月搞定计算机二级C语言——真题（9）解析11\-06收起
## 1\. 前言


本篇我们讲解[2个月搞定计算机二级C语言](https://github.com):[楚门加速器p](https://tianchuang88.com)——真题9


[![真题9-程序评分](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241106210732391-1265508167.png)](https://github.com)


## 2\. 程序填空题


### 2\.1 题目要求


[![真题9-程序填空](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241106210732229-1571276308.png)](https://github.com)


### 2\.2 提供的代码



```
#include  
double f1(double  x)
{
    return x * x;
}
double f2(double  x, double  y)
{
    return  x * y;
}
/**********found**********/
__1__ fun(int  i, double  x, double  y)
{
    if (i == 1)
        /**********found**********/
        return __2__(x);
    else
        /**********found**********/
        return  __3__(x, y);
}
main()
{
    double  x1 = 5, x2 = 3, r;
    r = fun(1, x1, x2);
    r += fun(2, x1, x2);
    printf("\nx1=%f, x2=%f, x1*x1+x1*x2=%f\n\n", x1, x2, r);
    getchar();
}

```

### 2\.3 解题思路


**第（1）处填空：**


题目要求输出浮点型，所以返回值可以使用`main`函数中使用的类型`double`。



```
double fun(int  i, double  x, double  y)

```

**第（2）处填空：**


这里填写的参数只有`x`，所以是调用的函数`f1`。



```
return f1(x);

```

**第（3）处填空：**


参数为`x,y`，对应着函数`f2`。



```
return  f2(x, y);

```

### 2\.4 代码实现


填写完整的代码：



```
#include  
double f1(double  x)
{
    return x * x;
}
double f2(double  x, double  y)
{
    return  x * y;
}
/**********found**********/
double fun(int  i, double  x, double  y)
{
    if (i == 1)
        /**********found**********/
        return f1(x);
    else
        /**********found**********/
        return  f2(x, y);
}
main()
{
    double  x1 = 5, x2 = 3, r;
    r = fun(1, x1, x2);
    r += fun(2, x1, x2);
    printf("\nx1=%f, x2=%f, x1*x1+x1*x2=%f\n\n", x1, x2, r);
    getchar();
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


## 3\. 程序修改题


### 3\.1 题目要求


[![真题9-程序修改](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241106210732254-920491501.png)](https://github.com)


### 3\.2 提供的代码



```
#include   
void fun(int  n)
{
    int  j, b, c, m, flag = 0;
    for (b = 1; b <= n / 2; b++) {
        /**********found**********/
        n = m;
        c = b;
        while (m != 0 && m >= c) {
            /**********found**********/
            m = m - c;    c++
        }
        /**********found**********/
        if (m != 0)
        {
            printf("%d=", n);
            for (j = b; j < c - 1; j++)   printf("%d+", j);
            printf("%d\n", j);
            flag = 1;
        }
    }
    if (flag == 0)
        printf("不能分解\n");
}
main()
{
    int  n;
    printf("请输入一个整数 :   ");   scanf("%d", &n);
    fun(n);
    getchar();
}

```

### 3\.3 解题思路


**第（1）处修改：**


原来的程序是`n = m;`，因为`m`这个变量在定义时没有初始化，它内部存储的可能是垃圾值，赋值给`n`后会导致`n`不再存储传入的 100，而是存储的垃圾值，这没有实际的意义，反而会导致程序跑飞。


所以这里需要让`m`初始化为`n`，在`while (m != 0 && m >= c)`这个循环中不断从`m`中减去`c`（当前序列的值），并且让`c`递增以考虑下一个正整数。



```
m = n;

```

**第（2）处修改：**


C语言中每条语句是以`;`作为结束，在语句`c++`后面少了`;`，加上即可。



```
m = m - c;    c++;

```

**第（3）处修改：**


如果在`while (m != 0 && m >= c)`循环结束时，变量`m`的值为 0，说明通过不断减去当前的正整数`c`，正好将`m`减到 0。我们前面将`n`赋值给了`m`、`b`赋值给了`c`，这就意味着从`b`开始的连续正整数的和恰好等于`n`。


所以说如果`m`等于 0，代表找到了和为`n`的一组连续正整数，则进行相应的输出。



```
if (m == 0)

```

### 3\.4 代码实现


修改后的代码：



```
#include   
void fun(int  n)
{
    int  j, b, c, m, flag = 0;
    for (b = 1; b <= n / 2; b++) {
        /**********found**********/
        m = n;
        c = b;
        while (m != 0 && m >= c) {
            /**********found**********/
            m = m - c;    c++;
        }
        /**********found**********/
        if (m == 0)
        {
            printf("%d=", n);
            for (j = b; j < c - 1; j++)   printf("%d+", j);
            printf("%d\n", j);
            flag = 1;
        }
    }
    if (flag == 0)
        printf("不能分解\n");
}
main()
{
    int  n;
    printf("请输入一个整数 :   ");   scanf("%d", &n);
    fun(n);
    getchar();
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


## 4\. 程序设计题


### 4\.1 题目要求


[![真题9-程序设计](https://img2024.cnblogs.com/blog/2881477/202411/2881477-20241106210732421-827282701.png)](https://github.com)


### 4\.2 提供的代码



```
#include   
#include  
void NONO();
int  fun(char* t)
{

}

main()
{
    char  s[26];
    printf("请输入一个字母组成的字符串 :  "); gets(s);
    if (fun(s))  printf("%s 是由连续字母组成的字符串.\n", s);
    else   printf("%s 不是由连续字母组成的字符串!\n", s);
    NONO();
    getchar();
}

void NONO()
{/* 本函数用于打开文件，输入数据，调用函数，输出数据，关闭文件。 */
    FILE* fp, * wf;
    int i;
    char s[26], * p;

    fp = fopen("in.dat", "r");
    wf = fopen("out.dat", "w");
    for (i = 0; i < 10; i++) {
        fgets(s, 26, fp);
        p = strchr(s, '\n');
        if (p) *p = 0;
        if (fun(s)) fprintf(wf, "%s\n", s + 2);
        else  fprintf(wf, "%s\n", strrev(s));
    }
    fclose(fp);
    fclose(wf);
}

```

### 4\.3 解题思路


我给出了两种解法，第二种在文末，先来看第一种。


对于这个题，我们首先需要知道`t`所指字符串的首位是什么字母，也就是`t[0]`的值，这里我使用`char c = t[0]`来存储，在知道值后可以根据`t`的大小遍历它，同时每次进行`c++;`作为连续递增字母序列的比较，在循环中只要找到一次`t[i]`不等于`c`的值，就说明`t`所指字符串是不连续的，直接返回 0 即可。当遍历完所有的元素均相等，则说明是连续的递增字母序列，返回 1。


下面假设`t`所指的字符串是`acd`，进行不连续字符串程序的演示：



```
      i    c    t[i]
1.    0    a    a---- > 相等进行下一次
2.    1    b    c---- > 不相等返回 0

```

反之连续字符串会执行完`for`循环后，返回 1。


### 4\.4 代码实现


填写完整的代码：



```
#include   
#include  
void NONO();
int  fun(char* t)
{
    char c = t[0];
    int i = 0;

    for (i = 0; i < strlen(t); i++)
    {
        if (t[i] != c)    // 当检测到一处不相等时，说明不是连续递增的
        {
            return 0;    // 则返回 0
        }
        c++;
    }

    return 1; // 将字符串全部遍历，没有发现不相等的，返回 1
}

main()
{
    char  s[26];
    printf("请输入一个字母组成的字符串 :  "); gets(s);
    if (fun(s))  printf("%s 是由连续字母组成的字符串.\n", s);
    else   printf("%s 不是由连续字母组成的字符串!\n", s);
    NONO();
    getchar();
}

void NONO()
{/* 本函数用于打开文件，输入数据，调用函数，输出数据，关闭文件。 */
    FILE* fp, * wf;
    int i;
    char s[26], * p;

    fp = fopen("in.dat", "r");
    wf = fopen("out.dat", "w");
    for (i = 0; i < 10; i++) {
        fgets(s, 26, fp);
        p = strchr(s, '\n');
        if (p) *p = 0;
        if (fun(s)) fprintf(wf, "%s\n", s + 2);
        else  fprintf(wf, "%s\n", strrev(s));
    }
    fclose(fp);
    fclose(wf);
}

```

提示：为确保代码正常运行，请在题库编程环境的对应题目中进行测试和运行。


还有一种方法是先根据首位元素和长度生成一个连续的递增字母序列，使用函数`strcmp()`用`t`与之比较，也可以判断是否连续，下面给出代码供大家参考：



```
int  fun(char* t)
{
    char c[26] = { 0 };
    int i = 0;

    // 先根据 t[0]的值，和它的大小生产连续的递增字母序列
    c[0] = t[0];
    for (i = 0; i < strlen(t); i++)
    {
        c[i] = c[0] + i;
    }
    // 使用 strcmp() 函数判断这两个字符串是否相等
    if (strcmp(c, t) == 0)    // strcmp() 返回 0 则说明两个字符串相等
    {
        return 1;    // 则返回 1
    }
    else {
        return 0;    // 不相等的，返回 0
}

```

## 5\. 后记


本篇博客到这就结束了，如果您有疑问或建议欢迎您在留言区留言。


