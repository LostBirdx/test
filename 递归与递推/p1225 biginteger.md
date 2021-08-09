
难道每次的高精度都要写这么多的代码吗?我看人家的那个代码就很简单的,没有那么长,这么长只定义了一个数据类型,有点夸张了.

涉及到知识点的题目:
洛谷OJ[p1225](https://www.luogu.com.cn/problem/P1255)

#### bign数据类型的定义
```C++
struct bign(){
	int d[1000]; //这个数组的长度决定了bign的精度.
	int len;
	bign(){		//这个构造函数,如果bign的定义是全局的话,那么应该也可以不写
		memset(d, 0, sizeof(d));
		len = 0;
	
	}
};

```

#### bign和基础数据类型的转换

```C++
bign change(char str[])
{
	bign a;
	a.len = strlen(str);
	for(int i = 0; i < a.len; i++)
	{
		a.d[i] = str[a.len - i - 1] - '0';
	}
	return a;
}
```

具体的思路就是把字符串倒序输入给数组d,因为对于整数而言,前面的是高位.
#### bign 的加法
```C++
bign add(bign a, bign b){
	bign c;
	int carry = 0;
	for(int i = 0; i < a.len || i < b.len; i++){
		int temp = a.d[i] + b.d[i] + carry;
		c.d[c.len++] = temp % 10;//个位数留下
		carry = temp / 10; //进位留给下一次运算
	}
	if(carry != 0){
		c.d[c.len++] = carry;
	}
	return c;
}

```