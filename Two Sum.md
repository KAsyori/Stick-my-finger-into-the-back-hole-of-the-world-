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
        for (int j = i + 1; j < nums.length; j++) { //遍历数组
            if (nums[j] == target - nums[i]) {
                return new int[] { i, j };  //创建一个含有i，j两个元素的数组并返回给主函数
                 }
             }
        }
       return new int[] {0,0}; //就算最后结果一定是找得到两个数的，但是没有这个return编译器会报错。所以姑且在没有正确结果的时候返回了[0,0]
    }
}
```
## 总结
`这是期末考试的第一题，不同的是当初要求补全的是c语言的函数，所以要求用了指针，而且还会遇到子函数的内存空间会被释放这样的难关。但是因为java没有指针，直接返回数组反而要简单一些。而且java里的数组都是对象，可以像nums.length一样直接访问它的成员或者成员方法。我的java才刚刚起步，还远不能发挥这个语言本身的特点，需要勤加练习！！！`
