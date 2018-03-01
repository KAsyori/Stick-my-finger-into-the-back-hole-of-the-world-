# Remove Nth Node From End of List
## Description
Given a linked list, remove the nth node from the end of list and return its head.  

For example,  
```
Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
   ```
## 解题思路
在单向链表里，找到并删除倒数第n个元素  
思路一 ：  
第一次遍历链表找到长度  
第二次遍历链表去除节点  
思路二 ：  
在表头前连接n个假节点，设置两个指针分别从原表头，和假表头向后遍历，  
从原表头的指针的next是null的时候，移除从假表头出发的指针所指向的节点。
  
  我用这次选择用代码来实现思路二
## 代码
```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode temp = new ListNode(0);
        ListNode Head = temp; n --;
        while (n > 0) {
            temp.next = new ListNode(0);
            temp = temp.next;
            -- n;
        }
        temp.next = head;
        ListNode ans = head;
        while (head.next != null) {
            Head = Head.next;
            head = head.next;
        }
        if (Head.next == ans)
            ans = ans.next != null ? ans.next : null;
        else if (Head.next.next == null)
            Head.next = null;
        else
            Head.next = Head.next.next;
        return ans;
    }
}
```
## 总结
难点是处理要消除的节点在表头表尾的各种特殊情况。
