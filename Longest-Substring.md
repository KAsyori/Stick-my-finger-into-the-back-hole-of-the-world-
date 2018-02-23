# Longest Substring Without Repeating Characters
## Description
Given a string, find the length of the longest substring without repeating characters.  
### Example
```
Given "abcabcbb", the answer is "abc", which the length is 3.  

Given "bbbbb", the answer is "b", with the length of 1.  

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.  
## 解题思路
从头开始遍历字符串，只要字母不重复就保持计数，直到遇到重复的字母位置，结算一下。  
当整个字符串遍历完毕之后，返回最大的一个结果，这就是基础思路  
**但是**  
怎么才能确定一个字符重复了呢？，是在遍历过程中，对之前的遍历过的内容再检测依次吗？那样太麻烦了。  
**为每一个字母设置个计数器**，当计数器大于1时，中断对最长子串的计数  
或者更直接，设置一个数组，每个字母对应数组中的一个元素，这个元素反映的是这个字母在字符串中的最后位置（这样的话，角标就是ascii码了）  
这样每当发现一个字母的最后位置不是0的时候就可以开始下一轮计数了。（这个时候记得计数方法就是，当前位置角标-上一个未发现重复位置的角标）
## 代码
```java
import java.util.Scanner;
class Solution {
	public static void main (String[] args) {
		Scanner sc = new Scanner(System.in);
		String s = sc.nextLine();
		System.out.println("最长不重复子串长度为"+lengthOfLongestSubstring(s));
	}
	public static int lengthOfLongestSubstring(String s) {
		int result = 0;
		int [] a = new int[1000];
		for (int i = 0,j = 0;i < s.length();i ++) {
			j = (a[s.charAt(i)] > 0) ? Math.max(j,a[s.charAt(i)]):j;
			a[s.charAt(i)] = i + 1;
			result = Math.max(result,i - j + 1);
		}
		return result;
	}
}
```
