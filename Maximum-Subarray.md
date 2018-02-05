# Maximum Subarray
## Description
 Find the contiguous subarray within an array (containing at least one number) which has the largest sum.  
For example, given the array [-2,1,-3,4,-1,2,1,-5,4],  
the contiguous subarray [4,-1,2,1] has the largest sum = 6.   
## 解题思路
>1.生成全部的子数列，计算出全部的和
2.反复使用Math.max（）方法得到最大值
## 代码
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxAtLast = -2147483648,tempSum = 0;
		for (int i = 1;i <= nums.length;i ++) {
			for (int j = 0;j <= nums.length-i;j ++) {
				for (int p = j; p < j + i;p ++) {
					tempSum += nums[p];
					maxAtLast = Math.max(maxAtLast,tempSum);
				}
				tempSum = 0;
			}
		}
		return maxAtLast;
    }
}
```
然后果不其然我就**超时了**  
蛮力不行的话就只有取巧了，于是我开始思考和最大的子数列**应当还有什么性质**  
## 解题思路2.0
>1.从头开始慢慢扩张数列并求和  
2.需要一个变量来储存扩张过程中曾出现的最大和
3.当前面一整段数列与下一位的和都小于下一个数时，以下一个数作为开（这往往意味着前一段数列和为负数）
```java
public static int maxSubArray(int[] nums) {
    int maxSoFar=nums[0], maxEndingHere=nums[0];
    for (int i=1;i<nums.length;++i){
    	maxEndingHere= Math.max(maxEndingHere+nums[i],nums[i]);
    	maxSoFar=Math.max(maxSoFar, maxEndingHere);	
    }
    return maxSoFar;
}
```
## 总结
解法2.0所利用的到的和最大的子数列的形成逻辑就是，当前最大的数列只有和**相邻且和非负**的数列相加才能变得更大。   
