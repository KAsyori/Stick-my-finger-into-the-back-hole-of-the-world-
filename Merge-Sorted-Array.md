# Merge Sorted Array
## Description
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
## 解题思路
### 思路1
1.遍历两个数组  
2.找到nums的插入位置之后，用循环结构使nums1从这个位置开始全部向后移动  
**缺陷**操作麻烦  
### 思路2
1.一个循环把nums2依次补进nums1里  
2.对nums1用排序方法  
## 代码
**这次用选择排序**
```java
public static void merge(int[] nums1,int m,int[] nums2,int n) {
		for (int i = m,j = 0;i < m + n;i ++) {
			nums1[i] = nums2[j ++];
		}
		for(int i = 0;i < m + n;i ++) {
			int temp = i;
			for (int j = i;j < m + n;j ++) {
				if (nums1[j] < nums1[temp]) {
					temp = j;
				}
			}int temp1 = nums1[i];
			nums1[i] = nums1[temp];
			nums1[temp] = temp1;
		}
		System.out.println(Arrays.toString(nums1));
	}
```
## 总结
出题者为了防止我用思路2，极有可能给nums1设置一个大于n+m的长度，并随机赋值来打乱我的排序。  
所以我把排序范围限制在m+n的范围内了，而没有用length。
