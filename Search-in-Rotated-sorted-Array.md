# Search in Rotated Sorted Array
## Description
Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.  

(i.e., 0 1 2 4 5 6 7 might become 4 5 6 7 0 1 2).  

You are given a target value to search. If found in the array return its index, otherwise return -1.  
  
You may assume no duplicate exists in the array.  
## 思路
在一个不重复的，排列过并旋转过的数列里返回target 的角标看起来是很简单的。  
我第一时间想到的是直接遍历，然而这次我不会再写这样的代码了，因为肯定会**超时**的。  
对于一个进行过未知旋转的，排列过的数组，在使用**二分搜索法**的时候需要找到被旋转之前的最小值和最大值所在的角标，然后分而治之。
## 代码
```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0) return -1;
        int start = 0, end = nums.length - 1;
        while (start < end) {
        int mid = (start + end) / 2;
        if (nums[mid] > nums[end]) {  // eg. 3,4,5,6,1,2
            if (target > nums[mid] || target <= nums[end]) {
                start = mid + 1;
            } else {
                end = mid;
            }
        } else {  // eg. 5,6,1,2,3,4
            if (target > nums[mid] && target <= nums[end]) {
                start = mid + 1;
            } else {
                end = mid;
            }
        }
    }
    if (start == end && target != nums[start]) return -1;
    return start;
    }
}
```
## 总结
打代码的时候想了一下，没有必要找到首尾连接点之后再分而治之。
