# Remove Element
## Description
>Given an array and a value, remove all instances of that value in-place and return the new length.  
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.  
The order of elements can be changed. It doesn't matter what you leave beyond the new length.  
### Exmample
```
Given nums = [3,2,2,3], val = 3,  

Your function should return length = 2, with the first two elements of nums being 2.  

```
## 解题思路
1.遍历数组寻找被删除的目标并计数  
2.使后面的全部数据往前移动一格  
3.接着遍历的时候还要再判断一次目前指向的数据是否是要remove的数据  

## 代码
```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count = 0;
		for (int i = 0;i < nums.length - count;i ++) {
			if (nums[i] == val) {
				count ++;
				for (int j = i;j < nums.length - 1;j ++) {
					nums[j] = nums[j + 1];
				}
				i --;
			}
		}
		//for (int i = 0;i < nums.length - count; i ++) {
			//System.out.print(" " + nums[i]);
		//}
		return nums.length - count;
    }
}
```
## 总结
有了上一道题（移除排列好的数列的重复元素）的经验这道题的思路要清晰多了。虽然说题里说数组后面的部分变成怎么样也不关心，但是自己要记得**缩小遍历范围**否则可能会导致计数器重复计数。
