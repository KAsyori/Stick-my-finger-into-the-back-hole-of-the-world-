# Sqrt(X)
## Description
Implement int sqrt(int x).  
Compute and return the square root of x.  
x is guaranteed to be a non-negative integer.  
## Example
```
Input: 4  
Output: 2  
```
## 解题思路
这道题的仁慈之处就是限定了返回值是整型，而且是强转的整型，不是四舍五入的整型。  
那么如何计算一个数的平方根呢。  
首先处理一个特殊情况，** 小于4的正数的平方根一定为1 0的平方一定为0**  
用到一定的** 数学方法** 和 **递归**  
>sqrt(N) = 2/2sqrt(N) =2sqrt(1/4)sqrt(N) = 2sqrt(N/4)  
## 代码
···java
public int mySqrt(int x) {
    if(x < 4) return x == 0 ? 0 : 1;
    int res = 2 * mySqrt(x/4);
    if((res+1) * (res+1) <= x && (res+1) * (res+1) >= 0) return res+1;
    return res;
}
···
## 总结
一开始看见只是构造一个数学方法还以为遇到简单题了，结果如果不想到递归的话，我还真想不到平方根的特点是什么。  
因为一直以来我都是通过思考所求的返回值有怎样的**特点**来编写方法的。
