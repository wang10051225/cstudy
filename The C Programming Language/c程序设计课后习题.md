#c程序设计语言习题 #

----------
### 第2章 类型、运算符与表达式 ###
1. 编写一个程序以确定分别由 signed 及 unsigned 限定的 char、short、
int 与 long 类型变量的取值范围。采用打印标准头文件中的相应值以及直接计算两种方式实
现。后一种方法的实现较困难一些，因为要确定各种浮点类型的取值范围。
  
```
#include<stdio.h>
long long get_max_number(const char length);
long long get_max_number(const char length)
{
	int loop;
	long long max_number = 1;
	for (loop = 0; loop < length * 8; loop++)
	{
		max_number *= 2;
	}
	return max_number - 1;
}

void show_type_range(const char*, const long long min, const long long max);
void show_type_range(const char* type, const long long min, const long long max)
{
	printf("%s: min:%lld, max:%lld\n", type, min, max);
}
int main()
{
	char length_of_char = sizeof(char);
	char length_of_short = sizeof(short);
	char length_of_int = sizeof(int);
	char length_of_long = sizeof(long);
	long long max_number_of_unsigned_char = get_max_number(length_of_char);
	show_type_range("unsigned char", 0, max_number_of_unsigned_char);
	show_type_range("signed char", 0 - max_number_of_unsigned_char/2, max_number_of_unsigned_char/2+1);
	long long max_number_of_unsigned_short = get_max_number(length_of_short);
	show_type_range("unsigned short", 0, max_number_of_unsigned_short);
	show_type_range("signed short", 0 - max_number_of_unsigned_short / 2, max_number_of_unsigned_short / 2 + 1);
	long long max_number_of_unsigned_int = get_max_number(length_of_int);
	show_type_range("unsigned int", 0, max_number_of_unsigned_int);
	show_type_range("signed int", 0 - max_number_of_unsigned_int / 2, max_number_of_unsigned_int / 2 + 1);
	long long max_number_of_unsigned_long = get_max_number(length_of_long);
	show_type_range("unsigned long", 0, max_number_of_unsigned_long);
	show_type_range("signed long", 0 - max_number_of_unsigned_long / 2, max_number_of_unsigned_long / 2 + 1);
	getchar();
	return 0;
}
```

#### 结果 ####
