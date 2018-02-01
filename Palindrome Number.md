# Palindrome Number
## Description
Determine whether an integer is a palindrome. Do this without extra space.
## 解题思路
拿着这个题我首先去百度了一下什么是**palindrome**
！[回型文](https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Sator_Square_at_Opp%C3%A8de.jpg/220px-Sator_Square_at_Opp%C3%A8de.jpg)
**回型文**就是正序倒序排列都不会变的文字，这样的话*负数肯定不是回型文*。
本题的要求补全的函数的参数是int型的而不是String类的，而且要求我不能使用*”extra space“*，但是我这个人**比较皮**，之前已经做过反转32位整型数的题了，这次其实只需要先pass掉负数，然后比较反转前反转后是否一样就可以了。本着练习java的**String类的使用**的初衷，我还是用了字符串的解法。
即转化为字符串之后，依次比较**对称位置上的字符是否相同**。
## 代码
```java
import java.util.Scanner;
class Solution {
	public static boolean isPalindrome (int x) {
		int i = 0; 
		if (x < 0)
			return false;//直接pass掉负数
		String Number = String.valueOf(x);//转化为String类
//		System.out.println(Number);
		while ( i <= Number.length() / 2 - 1) {//String类的length（）方法会直接返回字符串长度
			if (Number.charAt(i) != Number.charAt(Number.length() - i-1)) {//charAt（）方法，返回值是字符串对应位置的字符，从0开始，到length（）-1结束。
					return false;
					}
					else
					i ++;
					}
		return true;
		}
	public static void main (String [] args) {
		Scanner cin = new Scanner(System.in);
		int x = cin.nextInt();
//		System.out.println(x);
		System.out.println(isPalindrome(x));
	}
}
```
## 总结
有的时候，为了防止数据溢出，转化为字符串来处理是一个相当取巧的方法，这道题里练习到了String类里的诸多成员方法。
