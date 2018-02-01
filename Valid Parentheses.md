# Valid Parentheses.md
## Desctiption
>Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.
## 解题方法
首先我知道这个题**如果用栈来做的话简单得不得了**因为匹配括号的原理，和**进栈，出栈**的操作相当契合。  
但是我要用最原始的方法挑战这道题，数据结构的方法留着以后再说！  
最原始的思路  
1.({[为左边的一类，]})为右边的一类，如果先找左边的一类的话，在匹配右边的一类的时候会经过同样的很多的左边的一类，这样需要用**计数器对目前正在匹配的这个符号的个数计数，直到计数器复原的时候找到的右边的一类才是匹配的对象**这也是我以前走的弯路，其实先找到右边的一类，再往回找到第一个左边的一类就匹配了  
2.将匹配好的括号以其他字符替代，**避免重复匹配**  
3.设置判断语句，一旦遇到往回匹配的**路上有没有被替换的括号**，立刻判断为不匹配，返回 false。  
## 代码
```java
class Solution {
	public static boolean isValid (String s) {
		char[] c = s.toCharArray();//String类转字符数组以便对字符进行操作（String类对单个字符的替换并不方便）
		for (int i = 0 ;i < c.length;i++) {
			switch (c[i]) {
				case ')':                               //找到右边的一类
					for (int j = i-1;j >=0;j --) {        //往回匹配
						if (c[j] == '(') {                  //找到对象，两人私奔
							c[j] = '0';   
							c[i] = '0';
							break;                              
						}else if (c[j] != '0' && c[j] !='(') //路上遇到第三者，私奔失败
							return false;
					}
					break;
				case ']':
					for (int j = i-1;j >= 0;j --) {
						if (c[j] == '[') {
							c[j] = '0';
							c[i] = '0';
							break;
						}else if (c[j] != '0' && c[j] != '[')
							return false;
					}
					break;
				case '}':
					for (int j = i-1;j >=0 ;j --) {
						if (c[j] == '{') {
							c[j] = '0';
							c[i] = '0';
							break;
						}else if (c[j] != '0' && c[j] != '{')
							return false;
					}
					break;
			}
		}
		for (int i = 0;i < c.length;i ++)
			if (c[i] != '0')                      //如果一轮匹配完毕还有落单的括号，说明不匹配
				return false;
		return true;
	}
}
```
## 总结
明天我还是试着学学堆栈吧，原始方法做得我欲哭无泪～～～
