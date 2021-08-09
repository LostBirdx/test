其实总体来说记忆化搜索和你想的是一样的，就是把搜索的过程中的值用一个数组存起来 ，供后续的搜索过程使用。这样可以减少递推的时间复杂度。


[p1464 function](https://www.luogu.com.cn/problem/P1464)

<span style="font-family:default; font-size:default; color:#00ff7b">那几个数据类型的遍界值都是多少啊，每次都忘记了。</span>
https://blog.csdn.net/oadjing/article/details/48301327
```c++
#include <iostream>
#include <climits>
#include <cfloat>

using namespace std;

int main() {
    cout << "int 最大值：" << INT_MAX << '\n';
    cout << "int 最小值：" << INT_MIN << '\n';
    cout << "float 最大值：" << FLT_MAX << '\n';
    cout << "float 最小值：" << FLT_MIN << '\n';
    cout << "double 最大值：" << DBL_MAX << '\n';
    cout << "double 最小值：" << DBL_MIN << '\n';
    cout << "long 最大值：" << LONG_MAX << '\n';
    cout << "long 最小值：" << LONG_MIN << '\n';
    cout << "long long 最大值：" << LONG_LONG_MAX << '\n';
    cout << "long long 最小值：" << LONG_LONG_MIN << '\n';
    cout << "unsigned long long 最大值：" << ULONG_LONG_MAX << '\n';
}
```

运行结果：
```c++

int 最大值：2147483647
int 最小值：-2147483648
float 最大值：3.40282e+38
float 最小值：1.17549e-38
double 最大值：1.79769e+308
double 最小值：2.22507e-308
long 最大值：9223372036854775807
long 最小值：-9223372036854775808
long long 最大值：9223372036854775807
long long 最小值：-9223372036854775808
unsigned long long 最大值：18446744073709551615
```

<span style="font-family:default; font-size:default; color:#00ff7b">long 和long long 一样大吗？</span> 
在我的编译器上面，int 和long 一样大啊。

<font color = 'red'> usigned long long 最大值$10^{20}$</font>

![[Pasted image 20210322083323.png]]
---

<span style="font-family:default; font-size:default; color:#00ff84">定义long long int 时候能不能写long long  啊。</span>
是可以的。事实上用下面的代码是最好的。
```c++
typedef long long  ll;

```

连续输入的输入方式

```c++
 while(scanf("%lld%lld%lld",&a,&b,&c)==3){ // 这里可以学习一下。

	 memset(ans, 0, sizeof(ans));

	 if(a == -1 && b == -1 && c == -1)break;

	 printf("w(%lld, %lld, %lld)=", a, b, c);

	 if(a\>20) a\=21;

	 if(b\>20) b\=21;

	 if(c\>20) c\=21;

	 printf("%lld\\n", w(a, b, c));

 }
```

题目的要求是连续输入，以 -1,-1,-1结束，这里用了while(scanf("%llld%lld%lld",&a, &b, &c) == 3).

是因为scanf 读取成功时返回参数的个数。