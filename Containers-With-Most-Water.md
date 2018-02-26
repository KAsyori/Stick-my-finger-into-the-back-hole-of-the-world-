# Description
Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai).  
n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0).  
Find two lines, which together with x-axis forms a container, such that the container contains the most water.
## 思路
首先想象一个二位直角坐标系。  
我们输入的每一个元素的角标代表在横坐标上的位置，数值代表纵坐标的位置，这样的一个点对x轴作垂线。  
现在找两个这种垂线构成最大的容器。  
也就是说要同时考虑到横坐标之间的距离，和短板效应。  
所以我先想到的是遍历全部容器。
### 容器容积的计算方法
用i和j来表示两个角标的话，
S = (j - i) * Math.min(a[i],a[j]);
## 代码
```java
class Solution {
    public int maxArea(int[] height) {
        int res = Integer.MIN_VALUE;
        for (int i = 0;i < height.length - 1;i ++) {
            for(int j = i + 1;j < height.length;j ++) {
                res = (j - i) * Math.min(height[i],height[j]) > res ? (j-i)*Math.min(height[i],height[j]) : res;
                }
            }
        return res;
      }
}
```
当然这种代码一定会导致超时就对了。
## 新思路
**从短板效应**来思考这个问题，想办法节约遍历的次数。  
我们总是以短的一边作为高度，高度确定的情况下，横坐标距离要尽量远。所以这次不妨也试试从两边向中间缩圈的办法。  
初始的0和length - 1是横坐标差最大的情况，要想要更大的容量的话，只有移动短边的横坐标看能不能找到纵坐标更大的元素。  
## 代码
```java
class Solution {
    public int maxArea(int[] height) {
        int maxnow = Integer.MIN_VALUE;
        int left = 0; int right = height.length - 1;
        while(left < right ){
            maxnow = (right - left) * Math.min(height[left],height[right]) > maxnow ? (right - left) * Math.min(height[left],height[right]) : maxnow;
            if (height[left] < height [right]) left ++;
            else right --;
        }
        return maxnow;
    }
}
```
## 总结
*很多时候暴力并不能解决问题
