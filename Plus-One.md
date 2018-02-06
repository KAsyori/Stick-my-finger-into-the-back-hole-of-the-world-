# Plus One
## Description
Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.  
You may assume the integer do not contain any leading zero, except the number 0 itself.  
The digits are stored such that the most significant digit is at the head of the list.  
### No Example
## 解题思路
按照此题的题意，输入是一个表示**一个整数数组**这个数组的从0到length-1位是整数的第length位到个位。而现在我们要做的是给这个**整数**加一  
步骤如下：  
反向遍历数组
1.如果这一位不需要进位的话，直接+1并返回  
2.如果需要进位的话，就讲这一位归零，并给下一位+1。  
反向遍历的过程中，只有1和2两种可能性。因此代码相当简单。  
## 代码
``` java
public int[] plusOne(int[] digits) {
        
    int n = digits.length;
    for(int i=n-1; i>=0; i--) {
        if(digits[i] < 9) {
            digits[i]++;
            return digits;
        }
        
        digits[i] = 0;
    }
    
    int[] newNumber = new int [n+1];
    newNumber[0] = 1;
    
    return newNumber;
}
```
## 总结
这道题重要的还是题意的理解，没给实例很难理解啊
