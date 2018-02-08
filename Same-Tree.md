# Same Tree
## Description
 Given two binary trees, write a function to check if they are the same or not.  
Two binary trees are considered the same if they are structurally identical and the nodes have the same value.   
### Example 1:
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```
### Example 2:
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```
### Example 3:
```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```
## 思路
第一次接触数据结构的二叉树，《数据结构》我还没有系统的学过，今天也只是翻阅了一下二叉树的遍历而已。  
### 思路一
分别得到两个树的前序遍历序列和中序遍历序列*因为树上说任何含有n个节点的二叉树都可以由它的前序遍历序列和中序遍历序列唯一确定*  
那么前序遍历序列和中序遍历序列都一样的两个树就是一样的。
**缺点**：不知道总的节点数因而只能申请尽量长的数组，然后通过计数器来决定用于比较的部分
### 代码Accept
```java
class Solution {
	int count = 0;                        //因为遍历二叉树要用递归，所以数组和计数器全都创建的全局变量
	int[] preOrderArrayP = new int[1000];
	int[] preOrderArrayQ = new int[1000];
	int[] inOrderArrayP = new int[1000];
	int[] inOrderArrayQ = new int[1000];
	public boolean isSameTree(TreeNode p,TreeNode q) {
        if (p == null || q == null) return (p == q);
		createPOP(p);                       //依次调用生成序列用的方法
		count = 0;
		createPOQ(q);
		count = 0;
		createIOP(p);
		count = 0;
		createIOQ(q);
		if (Arrays.equals(preOrderArrayP,preOrderArrayQ) && Arrays.equals(inOrderArrayP,inOrderArrayQ))//来自jjava.util.Arrays包的比较数组的方法
			return true;
		else
			return false;
	}
	public void createPOP(TreeNode p) {
		if (p != null) {
			preOrderArrayP[count++] = p.val;
			createPOP(p.left);
			createPOP(p.right);
		}else{
            preOrderArrayP[count++] = 999;//null的部分用特殊字符代替，我量它的不可能恰好测试999吧
        }
	}
	public void createPOQ(TreeNode q) {
		if (q != null) {
			preOrderArrayQ[count++] = q.val;
			createPOQ(q.left);
			createPOQ(q.right);
		}else{
            preOrderArrayQ[count++] = 999;
        }
	}
	public void createIOP(TreeNode p) {
		if (p != null) {
			createIOP(p.left);
			inOrderArrayP[count++] = p.val;
			createIOP(p.right);
		}else{
            inOrderArrayP[count++] = 999;
        }
	}
	public void createIOQ(TreeNode q) {
		if (q != null) {
			createIOQ(q.left);
			inOrderArrayQ[count++] = q.val;
			createIOQ(q.right);
		}else{
            inOrderArrayQ[count++] = 999;
        }
	}
}
```
#### 总结
这个方法太粗暴，而且不简单，runtime = 7ms，是所有submition当中差不多最低的了。
## 思路二
一层一层的比较，一旦有一层不同就直接返回false。
### 代码Accepted
```java
public boolean isSameTree(TreeNode p, TreeNode q) {
    if(p == null && q == null) return true;
    if(p == null || q == null) return false;
    if(p.val == q.val)
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    return false;
}
```
#### 总结
这个就比较有灵性了，毕竟是新知识，上一个思路太拘泥于树上学得的内容没有对二叉树这个结构有深刻的理解。

