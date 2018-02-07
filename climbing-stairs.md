# Climbing Stairs
## Description
You are climbing a stair case. It takes n steps to reach to the top.  
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?   
### Example:
```
Input: 3
Output:  3
Explanation:  There are three ways to climb to the top.

1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```
## 解题思路
>（我曾经产生了用排列组合来做这道题的错觉）

### 思路一
使每一步都有跨一步或者两步两种可能，用递归去做
#### 代码
```java
class Solution {
    public int climbStairs(int n) {
        climb_Stairs(0, n);
    }
    public int climb_Stairs(int i, int n) {
        if (i > n) {
            return 0;
        }
        if (i == n) {
            return 1;
        }
        return climb_Stairs(i + 1, n) + climb_Stairs(i + 2, n);
    }
}
```
但是这样的话**会超时**  
### 思路二
用很多用递归做的事情，循环也能做  
递归的思路简单明了地去模拟题目描述的事件，用循环则需要换个视角  
走到第n阶的所有情况，可以看成在n-1阶的位置一步走1阶的情况+在n-2阶的位置一步走了2阶的情况  
这样**依次类推**可以一直推到n = 1和n = 2的情况，而这两个我们很轻易就能知道答案是1和2。所以代码应该这么写
#### 代码
```java
import java.util.Scanner;
class Solution {
	public static int climbStairs(int n) {
		if (n == 1) {
			return 1;
		}
		int [] dp = new int[n + 1];
		dp[1] = 1;
		dp[2] = 2;
		for (int i = 3;i <= n;i ++) {
			dp[i] = dp[i - 1] + dp[i - 2];
		}
		return dp[n];
	}
	public static void main (String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		System.out.println("有"+climbStairs(n)+"种情况");
	}
}
```
## 总结
递归的时候容易忘记设置停止条件~~虽然最后还是超时了~~
打完这个循环的代码，才发现这个原来是以前做过的题。所谓温故而之新嘛，~~这说明上次看题解的时候没看明白（dp是动态规划的意思）~~
