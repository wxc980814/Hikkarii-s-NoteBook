# const定义常量必须初始化 
```cpp
const int a;//error
```
# 与指针相关的四种const
```cpp
const char* a;//指向const对象的指针或者说指向常量的指针。
char const* a;//同上
char* const a;//指向类型对象的const指针。或者说常指针、const指针。
const char* const a;//指向const对象的const指针。
```
前两种等价
**着重看const与\*之间的位置**
·const在\*左边：const修饰的是指针指向的变量（也就是指针指向一个常量）
·const在\*右边：const修饰指针本身，指针的值不能修改（也就是指向的变量不能改，但是变量的值是可以改的）

###  指向常量的指针
```cpp
	const int* ptr;
	const int a = 10;
	ptr = &a; 
```
ptr是一个指向int类型const对象的指针，const定义的是int类型，也就是ptr所指向的对象类型，而不是ptr本身，所以ptr可以不用赋初始值。

其中，a前面的const也可以不要，**可以使用非const对象的地址赋值给const对象的指针**
### 常指针
```cpp
#include<iostream>
using namespace std;
int main() {

	int num = 0;
	int aaa = 2;
	int* const ptr = &num; 
	//ptr = &aaa;//error ：表达式必须是可修改的左值
	int* t = &num;
	*t = 1;
	cout << *ptr << endl;
	system("pause");
}
```
输出为1
在