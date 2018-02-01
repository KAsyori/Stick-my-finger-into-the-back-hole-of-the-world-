# Two Sum
## Description
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
## Example
` Given nums = [2,7,11,15,], target = 9,
  Because nums[0] + nums[1] = 2 + 7 =9,
  return [0,1].
  `
 ## 解题思路
  遍历数组寻找**和为target的两个元素**，并记录其下标，放在**数组**里，返回给主函数。
 ## 代码
 ```java
   class Solution {
   public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        for (int j = i + 1; j < nums.length; j++) {
            if (nums[j] == target - nums[i]) {
                return new int[] { i, j };
                 }
             }
        }
       return new int[] {0,0};
    }
}
```
