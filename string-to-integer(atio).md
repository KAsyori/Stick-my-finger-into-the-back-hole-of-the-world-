# String to Integer(atio)
## Description
Implement atoi to convert a string to an integer.
## 解题思路
这道题其实是然我们自己写一个atio的函数，来实现字符串到整型的转化，从**模板的方法名称**就能看出来题意。  
所以我估计很多人啊，可能直接用这个方法就ac了  
这道题很气人的地方是**没有一个示例**，全是英文对atio的解释。总结下来有一下要求  
~~1.不能义气用事！~~  
1.去掉字符串前后多余的空格  
2.记录下字符串所代表的整型数的符号
3.遇到非数字的字符直接中断  
4.当字符串表示的数比integer的范围大时返回最大最小值  
## 代码
```java
class Solution {
    public int myAtoi(String str) {
        if (str == null || str.length() == 0)
			return 0;
		str = str.trim();
		boolean positive = true;
		int i = 0;
		if (str.charAt(0) == '+') {
			i++;
		}else if (str.charAt(0) == '-') {
			positive = false;
			i ++;
		}
		double temp = 0;
		for (;i < str.length();i ++) {
			int digit = str.charAt(i) - '0';
			if (digit < 0 || digit > 9) 
				break;
			if (positive) {
				temp = 10*temp + digit;
				if(temp > Integer.MAX_VALUE) return Integer.MAX_VALUE;
			}else{
				temp = 10*temp - digit;
				if (temp < Integer.MIN_VALUE) return Integer.MIN_VALUE;
			}
		}
		int result = (int)temp;
		return result;
    }
}
```
## 总结
没有example，runcode也只是测试了**字符长度为0的情况**（字符串长度为0和字符串为空是两种情况），其余的就像在打补丁一样，Submit错一次，发现一个问题。  
这次也是破天荒想到了用ascii码相减来排除找到异常字符。这么多天不打代码，思维确实有点僵化了。
