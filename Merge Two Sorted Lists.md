# Merge Two Sorted Lists
## Description
Merge two sorted linked lists and return it as a new list.The new list should be made by  
splicing together the nodes of the first two lists
### Example
>**Inpu**t: 1->2->4, 1->3->4
 **Output**: 1->1->2->3->4->4
 ## 解题思路
 >两个已经排序好了的链表组合起来，我们一定要用好它**已经排序好**的这个特点。我可以用一个链表，插入另一个链表。  
 今天也复习了一下链表的知识，试试看在java这种**不能调用指针**的语言里，链表应该怎么用吧。  
 其实处理两个链表挺简单的，但是在自己的电脑上测试代码，还是要自己创建一个动态链表。这个花费了大量的时间。
 ### ListNode
 这是java里单向链表的基本形式
 ```java
 class ListNode {
	int val;
	ListNode next;
	ListNode (int x) { val = x; }
}
```
### dummyHead
一般创建链表的时候用一个
```java
dummyHead = new ListNode(0);
```
可以有效的防止出现头节点为空的情况，返回值写dummyHead.next，意味着不用储存头节点。
## 代码
```java
import java.util.Scanner;
class ListNode {//创建链表的类
	int val;
	ListNode next;
	ListNode (int x) { val = x; }
}
class Solution {
	public static ListNode mergeTwoLists (ListNode l1,ListNode l2) {
		ListNode dummyHead = new ListNode(0);
		if (l1 == null)
			return l2;//处理输入的值为空的情况
		if (l2 == null)
			return l1;
		ListNode p = (l1.val >= l2.val)? l2:l1;//决定谁插谁，但是后来发现貌似没有这个必要
		ListNode q = (l1.val >= l2.val)? l1:l2;
		dummyHead.next = p;
		while (p != null && q != null) {//防止出现调用空节点的成员的错误
			if (p.next != null && p.next.val >=  q.val) {//总是将当前q指向的节点，数值比自身大的第一个节点之前
				ListNode temp = p.next;
				p.next = q;
				q = q.next;
				p.next.next = temp;
			}
			else if (p.next == null) {//当被插入的链表已经到头了以后，插入的链表将剩余的元素直接接在被插入的链表之后
				p.next = q;
				break;
			}
			else
				p = p.next;
		}
		return dummyHead.next;
	}
	public static void main (String[] args) {//搞定链表的输入问题
		ListNode l1 = new ListNode(0); ListNode l2 = new ListNode(0);
		Scanner sc = new Scanner(System.in);
		ListNode temp = /*new*/ l1;
		System.out.println ("请输入一串排序好的数列，用空格分开，以0结束");
		while(true) {
			int t = sc.nextInt();
			if(t == 0) {
				break;
			}else{
				temp.next = new ListNode(0);
				temp = /*new*/ temp.next;
				temp.val = t
			}
		}
		temp =/*new*/ l2;
		System.out.println("请输入另一串排序好的数列，用空格分开，以0结束");
		while(true) {
			int t = sc.nextInt();
			if (t == 0) {
				break;
			}else{
				temp.next = new ListNode (0);
				temp = /*new*/ temp.next;
				temp.val = t;
			}
		}
		ListNode res = mergeTwoLists (l1.next , l2.next);
		System.out.println("下面是得到的结果");
		while (res != null) {
			System.out.print (" "+res.val);
			res = res.next;
		}
	}
}
```
## 总结
链表类的题，最重要的就是拆节点的时候不要乱，要小心**和数组越界类似的**访问到空节点的事情发生。做好各种防止bug的措施（*比如空节点*）
