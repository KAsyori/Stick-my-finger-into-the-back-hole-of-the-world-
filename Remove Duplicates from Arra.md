# Remove Duplicates from Sorted Array
## Description
>Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
### Example
```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
```
## 解题思路
*只允许在一个数组里*操作，做这道题只需要两步：  
1.遍历一遍数组  
2.用计数器记下重复的数字的个数，返回length-count。  
*但是我发现它检查的是我的数组的前几项是否已经如题意一样remove了重复的数字*  
所以再加一步  
3.添加一个指向数组第一项的指针，每当发现不重复的項，指针向后移一位，并将不重复的值赋给这一位。
## 代码
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int count = 0;
		int i = 0;
		for (int j = i + 1; j < nums.length;j ++) {
			if (nums[j] == nums[i]) {
				count ++;
			}else{
                i++;
				nums[i] = nums[j];
			}
		}	
		return nums.length - count;
    }
}
```
## 总结
这道题主要是一开始读题出了问题，浪费了一点时间。  
回过头再看一遍代码，发现计数器其实可以去掉，返回值变成i + 1就行了。
