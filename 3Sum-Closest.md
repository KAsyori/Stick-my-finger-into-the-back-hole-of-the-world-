# 3Sum Closest
## Description
Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target.  
Return the sum of the three integers. You may assume that each input would have exactly one solution.
### Example
```
  For example, given array S = {-1 2 1 -4}, and target = 1.

    The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```
## 思路
寻找最接近目标的三个数的和，那么如果只给三个数就可以直接出结果了。  
为了方便计算，先把给的数列排序一下，然后从两边往中间靠拢计算
## 代码
```java
class Solution {
    public int threeSumClosest(int[] num, int target) {
        int result = num[0] + num[1] + num[num.length - 1];
        Arrays.sort(num);
        for (int i = 0; i < num.length - 2; i++) {
            int start = i + 1, end = num.length - 1;
            while (start < end) {
                int sum = num[i] + num[start] + num[end];
                if (sum > target) {
                    end--;
                } else {
                    start++;
                }
                if (Math.abs(sum - target) < Math.abs(result - target)) {
                    result = sum;
                }
            }
        }
        return result;
    }
}
```
## 总结
原来的思路是遍历后算出所有3个组合数的和，保留与target差最小的。但是那样的代码极其花时间。  
用先排序，再从两边往中间找的方法可以大大节约循环次数。
