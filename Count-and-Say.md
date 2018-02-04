# Count and Say
## Description
>The count-and-say sequence is the sequence of integers with the first five terms as following:

```
1.     1  
2.     11  
3.     21  
4.     1211  
5.     111221  
```
> 1 is read off as "one 1" or 11.  
11 is read off as "two 1s" or 21.  
21 is read off as "one 2, then one 1" or 1211.  
Given an integer n, generate the nth term of the count-and-say sequence.  
Note: Each term of the sequence of integers will be represented as a string. 
### Example 1 :
```
Input: 1
Output: "1"
```
### Example 2:
```
Input: 4
Output: "1211"
```
## 解题思路
一开始看完全看不懂～～～  
我一开始以为是
给我一个数字，我要把它转化成由"1""11"和"21"构成的字符串  
其中 1 stands for 1  
    11 stands for 2  
    21 stands for 3  
但是看了 5 = 111221之后又发现不止这三个。
要做出这道题，必须理解**Count and Say**的题意。
于是我抄下了discuss区里发布的一个代码，在电脑上改了一下之后生成了1～10的对应的输出  
1  
11  
21  
1211  
111221  
312211  
13112221  
1113213211  
31131211131221  
13211311123113112211  
才**恍然大悟**，原来*左边的序号，和右边的字符串并没有序号关系，只是表示这个字符串在这整个序列当中的位置而已*  
而这个个序列的生成规律就是：**下一个字符串，是把上一个字符串读出来之后的形式**  
比如说第4行的1211，就是1个1，1个2和2个1，即第5行的111221。
那么要做出这道题就太简单了。
1.因为输入只有字符串所在的行数，所以我们自己写的代码，必须能够生成从1到n行的全部字符串才行，因为**每一行都是上一行的”读作“**。  
2.写的代码要完成的任务就是：*对相邻相同的数进行计数，生成结果为‘int 几个’‘int 几’形式的字符串*  
3.将步骤2中生成的字符串依次拼接。  
## 代码
因为是用的java，所以再用以前学c的时候的字符串数组来处理的话就得不偿失了，所以java的代码必须要反映出java作为一个**半面向对象的  
编程语言的优势特色。**  
因而这次我准备用到**对单个字符串变量进行处理的** `StringBuilder类`，这个类也在lang包里，不需要额外导入其他的包。其特点是能随意在这  
个类生成的字符串的末尾，中间进行添加插入字符串的操作，并且会自动更变字符串长度。和String类的对象不同的是，String类的对象是常量，虽然  
String类也有更改字符串的方法，但是它*只是按照要求生成了一个新的同名字符串取代了原字符串而已*，因此运行速度比StringBuilder要慢得多。
```java
class Solution {
    public String countAndSay(int n) {
        String str = "1";
        for (int i = 1; i < n; i++) {//输入1的时候无法进入循环，会返回初始的s，即”1“
            StringBuilder sb = new StringBuilder();
            for (int j = 1, count = 1; j <= str.length(); j++) {//j是指向当前位置的指针，count是计算相同数字的计数器。
                if (j == s.length() || str.charAt(j - 1) != str.charAt(j)) {//结束对连续相同数字计数的两种情况1.找到不一样的数2.到字符串末端
                    sb.append(count);   //这个方法的作用是在字符串末端拼接上括号里的数字，能够实现类型转换
                    sb.append(str.charAt(j - 1));
                    count = 1;//计数完毕之后不要忘了重置
                } else {
                    count++;//计数
                }
            }
            str = sb.toString();//更新字符串，此时的s的length也更新了。如果在此处打印s就能生成从2～n的整个序列了（1没进循环，作为特殊情况处理）
        }
        return str;
    }
}
```
## 总结
1.读题很重要，不要先入为主地思考问题，往往这样会浪费很多时间  
2.二次阅读自己的代码，精简当中的数量关系可以大大缩短代码的长度  
比如说这个代码一开始的时候把输入”1“作为一种特殊情况有
```java
if (n = 1)
return "1";
```
行数+2  
还专门申请了一个String类的对象来储存每次生成的新的字符串，其实不断反复使用str就行了的  

