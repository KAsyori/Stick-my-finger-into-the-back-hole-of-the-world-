# Single Number
## Description
Given an array of integers, every element appears twice except for one. Find that single one.
## 解题思路
(我跳过了几道二叉树的题改天再做）  
两个循环嵌套，返回没有重复的数  
## 代码
```java
class Solution {
    public int singleNumber(int[] nums) {
        boolean flag = false;
		for (int i = 0;i < nums.length;i ++) {
			for (int j = 0;j < nums.length;j ++) {
				if (nums[i] == nums[j] && i != j) {
					flag = true;
					break;
				}
			}
			if(flag == false) {
				return nums[i];
			}else{
				flag = false;
			}
		}
		throw new IllegalArgumentException("没有落单的数字");
    }
}
```
## 总结
因为写代码的时候编译器会考虑不符合题意的情况。，所以没有返回值的话编译器不给过，throw是java里抛出错误提示的语句可以用来代替return结束程序。
