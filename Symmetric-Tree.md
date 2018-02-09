# Symmetric Tree
## Description
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).  
For example, this binary tree [1,2,2,3,4,4,3] is symmetric:   
```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```
But the following [1,2,2,null,3,null,3] is not:  
```
    1
   / \
  2   2
   \   \
   3    3 
```
## 思路
可以用用昨天在Discus区学到的方法了  
1.首先验证root是否为null（因为leetcode日常验证空输入），为null就可以返回true了  
2.从第二层开始比较左右是否相等，第三层开始比较左边的左边和右边的右边是否相等，右边的左边和左边的右边是否相等  
可以用递归来实现  
## 代码
```java
class Solution {
	public boolean isSymmetric(TreeNode root) {
		if (root == null) {return true;}
		else if(isSymmetricTry(root.left,root.right))
			return true;
		else
			return false;
	}
	public boolean isSymmetricTry(TreeNode left,TreeNode right) {
		if (left == null || right == null) {
			return left == right;
		}
		if (left.val != right.val)
			return false;
		return isSymmetricTry(left.left,right.right) && isSymmetricTry(left.right,right.left);
	}
}
```
## 总结
这道题的做法是受到昨天的二叉树比较的启发，结合对称的树的特点想出来的方法。~~所以三种遍历方法到底有什么用（捂脸）~~  
需要注意的还是无处不在的空指针，java里可以比较这个对象是否为空，但是一旦调用空对象就会报错。而且从创建树的过程很麻烦，所以这些题我都没在电脑上测试.
