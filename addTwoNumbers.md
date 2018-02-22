# Add Two Numbers
## Description
You are given two **non-empty** linked lists representing two non-negative integers.  
The digits are stored in **reverse order** and each of their nodes contain a single digit.   
Add the two numbers and return it as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.
## Example
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.

```
## 解题思路
1.先用一个循环，将两个链表的长度调整一致，**原来是null的部分用val为0的ListNode型代替**  
2.长度一样了，就可以放心相加了  
**分类处理**  
对齐的位上val之和 < 10 时正常相加，放心移位  
大于10时，当前位之和减10，下一位进1**若下位不存在，就new一个val为0的next出来**  
3.返回链表头 over  
## 代码
```java
class Solution {
	public ListNode addTwoNumbers (ListNode l1,ListNode l2) {
		ListNode head = l1;ListNode temp = l2;
		while (true) {
			if (l1.next == null && l2.next != null)
				l1.next = new ListNode(0);
			if (l1.next != null && l2.next == null)
				l2.next = new ListNode(0);
			if (l1.next == l2.next && l1.next == null)
				break;
			else {
				l1 = l1.next;
				l2 = l2.next;
			}
		}
		l1 = head; l2 = temp;
		while (true) {
			if (l1.val + l2.val < 10) {
				l1.val += l2.val;
				if (l1.next != null) {
					l1 = l1.next;
					l2 = l2.next;
				}else break;
			}else{
				l1.val = l1.val + l2.val - 10;
				if (l1.next == null) {
					l1.next = new ListNode(0);
				}
				l1.next.val ++;
				if (l2.next != null) {
					l1 = l1.next;
					l2 = l2.next;
				}else break;
			}
		}
		return head;
	}
}
```
## 总结
采用了一个比较笨拙的办法，但是实际打起代码来却要放松一些，就是损失了一些运行速度。
