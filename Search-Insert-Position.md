# Search Insert Position
## Description
>Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.  
You may assume no duplicates in the array.  
### Example 1:
```
Input: [1,3,5,6], 5  
Output: 2  
```
### Example 2:
```
Input: [1,3,5,6], 2  
Output: 1  
```
### Example 3:
```
Input: [1,3,5,6], 7  
Output: 4  
```
### Example 4:
```
Input: [1,3,5,6], 0  
Output: 0  
```
## 解题思路：
既然题目给我们分了两种情况，那我们就按两种情况来处理呗  
1.遍历所给的数组，挨个比较寻找target  
2.遍历所给的数组，寻找第一个大于target的数  
3. 1 + 2 = 遍历所给的数组，寻找第一个大于等于taget的数的下标  
4.遍历完没有返回值的，返回数组长度nums.length。

## 代码：
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        for (int i = 0 ;i < nums.length; i ++) {
            if (nums [i] >= target) {
                return i ;
            }
        }
        return nums.length;
    }
}
```
## 总结
好像一不小心选到一道送分题
