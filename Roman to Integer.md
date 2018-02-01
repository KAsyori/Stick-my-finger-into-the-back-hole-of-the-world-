# Roman to Integer
## Description
`Given a roman numeral, convert it to an integer.
Input is guaranteed to be within the range from 1 to 3999.
`
## 解题思路
**还记得期末考试的时候写到崩溃的switch和break吗？？？  
  还记得思来向去也没有考虑到的特殊情况吗？？？  
  如果当时是时间不够，那给我足够的时间我能做出来吗？  
  能！**  
  其实一开始遇到这个题的时候我只是在单纯的思考代表1 10 100的罗马数字和代表5 50 500 1000的罗马数字之间的空间关系所导致的结果的不同  
  然后再思考其中的特殊情况。  
  但是如果从数值的方向去思考的话就会发现，罗马数字其实很严谨，没有特殊情况可言。  
  用” **I** “举个例子，罗马数字从左到右相加遇到 I的时候，如果相加得到的数字之和已经超过了5,那么I代表的一定是+1，否则是-1。  
  其他的也是相同的规律。  
  ## 代码
  ```java
class Solution {
public static int romanToInt(String s) {
	int res = 0;
	for (int i = s.length() - 1; i >= 0; i--) {
		char c = s.charAt(i);
		switch (c) {
		case 'I':
			res += (res >= 5 ? -1 : 1);//？：运算符，？左边的表达式为true时返回：右边的表达式的值，否则反之
			break;
		case 'V':
			res += 5;
			break;
		case 'X':
			res += 10 * (res >= 50 ? -1 : 1);
			break;
		case 'L':
			res += 50;
			break;
		case 'C':
			res += 100 * (res >= 500 ? -1 : 1);
			break;
		case 'D':
			res += 500;
			break;
		case 'M':
			res += 1000;
			break;
		}
	}
	return res;
}
}
```
## 总结
初次接触？：运算符的用法。大大简化了重复的操作。
[^footnote]:也是从题解里看到的。
