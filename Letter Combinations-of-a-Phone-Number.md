# Letter Combinations of a Phone Number
## Description
Given a digit string, return all possible letter combinations that the number could represent.  

A mapping of digit to letters (just like on the telephone buttons) is given below.  
## Example
```
Input:Digit string "23"  
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].  
```
## 解题思路
首先看见函数的返回值是个 List<String> 的时候，我就不得不去看了看集合框架的知识。然后简单的看了下List的用法，顺便了解了一下栈的概念。  
短短几小时的阅读不足以很快理解这些东西，这道题我选择在discuss区找个题解进行理解  
在那之前，我还是有我的思路的  
1. 给我一个含有n个元素的字符串，每个数字或者符号元素分别代表了一些字母或符号，我要设计函数返回这些字母或符号的全组合。  
2. 字母或符号和对应的数字绑定，首先我想到的应该是结构体数组。难点在于，如何形成n个字母一组元素，*因为直接使用list.add的话会视为  
直接添加了一个元素，而不是在元素中增加一个字母。*  
## 代码
```java
class Solution {
    public List<String> letterCombinations(String digits) {
        LinkedList<String> ans = new LinkedList<String>();
        if (digits.isEmpty()) return ans;
        String[] mapping = new String[] {"0","1","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
        ans.add("");
        for (int i = 0;i < digits.length();i++){
            int x = Character.getNumericValue(digits.charAt(i));
            while (ans.peek().length() == i) {
                String t = ans.remove();
                for (char s : mapping[x].toCharArray())
                    ans.add(t+s);
            }
        }
        return ans;
    }
}
```
### 代码分析
这个在discuss区看见的代码没有用结构体数组，而是用以“0“开头的String数组**使得字符串在数组中的角标与电话中的位置对应**  
那么解决我的思路中的难题的代码就是 
```java
String t = ans.remove;
```
这是一个迭代的解决方案。对于添加的每一个数字，**删除并复制队列中的每个元素**，并将可能的字母添加到每个元素中，然后再次将更新过的元素添加回队列中。  
重复这个过程，直到所有的数字都被重复。
