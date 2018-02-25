# Divide Two integers  
## Description
Divide two integers without using multiplication, division and mod operator.  
If it is overflow, return MAX_INT.  
## 思路
简单的说，不准用乘除法和mod运算符，写一个方法去实现除法。  
我这里用的是最简单的思路。  
先确定两个整数是否异号，以此来确定结果的符号  
然后都变为绝对值之后循环相减并计数，超过最大值就返回最大值，超过最小值同理。  
当然为了避免结果也overflow，计数的数要用double。
## 代码
···java
class Solution {
    public int divide(int dividend, int divisor) {
        boolean positive = true;
		if(dividend < 0) positive = (divisor < 0) ? true : false;
		else positive = (divisor > 0) ? true : false;
		dividend = (dividend < 0) ? -dividend : dividend;
		divisor = (divisor < 0) ? -divisor : divisor;
		double res = 0;
		while (true) {
			dividend -= divisor;
            if (dividend >= 0)
			    res ++;
            else
                break;
			if (res > Integer.MAX_VALUE) return (positive) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
		}
		int result =(int) res;
		return (positive) ? result : -result;
    }
}
···
## 总结
用这个方法在计算大数据的时候，比如int最大值除以1的时候会严重超时，但是目前没有找到更好的解决办法。
