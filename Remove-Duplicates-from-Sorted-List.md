# Remove Duplicates from Sorted List
## Description
 Given a sorted linked list, delete all duplicates such that each element appear only once.  
### Example
```
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3. 
```
## 思路
单向链表题  
1.比较链表前后的值是否相等  
2.相等则将下一位从链表中移除  
3.否则指针指向下一位  
## 代码
```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null){return null;}
        ListNode temp = head;
		while (head.next != null) {
			if (head.next.val == head.val) {
				if (head.next.next == null) {
					head.next = null;
					return temp;
				}else{
					head.next = head.next.next;
				}
			}else{
				head = head.next;
			}
		}
		return temp;
    }
}
```
## 总结
移除重复数字的链表版，注意点还是空指针和创建链表。
