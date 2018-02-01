# Reverse Integer
## Description
`Given a 32-bit signed integer,reverse digits of an integer.`
## Example 1:
  **Input**:123
  **output***:321
## Example 2:
   **Input**:-123
   **Output**:-321
 ## Example 3:
   **Input**:120
   **Output**:21
## Note:
   `Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows. `
## 解题思路
`从上面的Note可以看出，这道题的一个主要难点是在数据的“overflws”上，譬如2147483648这样站在长整型悬崖边上的数据，反转之后各位上的8一下子变到最高位去，自然就超出长整型的范围了。所以我们可以用范围更大的长长整型先暂存一下我们反转的结果，最后判断一下这个在不在32位整型数的范围之内，如果在就直接返回，如果不在就返回0.
其实鉴于java的String类可以很方便地实现整型和字符串的转换，这道题完全可以用另一种做法，但是为了迎合考点，这次我自始至终都在用long int和long long int解题。
`
## 代码
[^footnote]:（后来想起原来我这道题用的c++）
```c++
#include <iostream>
using namespace std;
int main () {
	long int x = 0;
	cin>>x;
	long int weishu[10000] = {0};
	int i = 0;long int divider = 1;//除数声明为long int是因为int型会导致long int的x被强转为int从而出现数据溢出，报错被除数为0的情况。
	//cout<< x <<endl;曾经用于检测此处的x的值
	while (x/divider != 0) {
		weishu[i] = x/divider - x/(divider*10)*10;//利用整型的特点，从个位开始依次获得每一位的数
		i ++; divider *= 10;
	}
	i--; divider /= 10;//把最后多加的减回去，其实现在想想，完全可以在后面的代码里把"<="换成"<"，把"divider /= 10"移动到循环开头来简化代码。
	long long int result = 0;
	for (int j = 0; j <= i;j ++) {
		result +=weishu[j] * divider;
		divider /= 10;
	}
	if (result >= - 2147483648 && result <=2147483648) {
		cout<<result<<endl;
		return result;
	}
	else {
		//cout<< 0 <<endl;
		return 0;//超出32位有符号整型的范围则返回0。
	}
}
```
## 总结
**一定要注意那些自动发生的强制类型转换**
