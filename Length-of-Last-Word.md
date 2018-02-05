# Length of Last Word
## Description 
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.  

If the last word does not exist, return 0.  
### Example:
```
Input: "Hello World"
Output: 5
```
## 解题思路
这非常简单。  
>1.用String.trim（）剪掉两边出现的非法空格
2.用String.lastIndexOf（‘ ’）从后往前搜索第一个空格  
3.返回字符串长度-空格角标-1;

## 代码
```java
class Solution {
    public int lengthOfLastWord(String s) {
        s = s.trim();
        return s.length()-s.lastIndexOf(' ')-1;
    }
}
```
## 总结
终于遇到两行代码就能解决的题了～～～～～～
