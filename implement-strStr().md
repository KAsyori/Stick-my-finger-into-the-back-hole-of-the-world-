# Implement strStr()
## Description
>Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.   
### Example 1
```
Input: haystack = "hello", needle = "ll"
Output: 2
```
### Example 2
```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```
## 解题思路
>这一看就是寻找字串嘛，思路很清晰了  
1.在遍历主串寻找与字串的头字符相同的字符，找不到就return -1，找到了先记录下角标  
2.找到之后，主串从该位置起和字串逐位比较，若字串遍历完成之前，主串先结束了或者有不同的字符，则返回 -1  
 否则返回1.中记录下的角标  
 
 ## 代码
 说得那么好听，奈何String类自带寻找字串的方法啊
 ```java
 lass Solution {
    public int strStr(String haystack, String needle) {
        int index = haystack.indexOf(needle);
        return index;
    }
}
```
## 总结
String类真好用～～～～～～～～～～～
