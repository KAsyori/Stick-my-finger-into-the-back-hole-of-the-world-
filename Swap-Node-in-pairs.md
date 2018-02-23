# Swap Node in Pairs
## Description
Given a linked list, swap every two adjacent nodes and return its head. 
简单的说，就是要在单向链表里面，两个一组进行交换，而且禁止我直接交换数值，必须把整个节点都交换才行
## 思路
每个节点只认得自己的下一个节点的话，要交换节点就意味着
head.next = head.next.next  
head.next.next = head  
**就这么绕一下就很晕了**，所以要用到之前用过的“假头",先把链表头给固定下来。
## 代码
```java
public class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode cur = head;
        ListNode newHead = head.next;
        while (cur != null && cur.next != null) {
            ListNode tmp = cur;
            cur = cur.next;
            tmp.next = cur.next;
            cur.next = tmp;
            cur = tmp.next;
            if (cur != null && cur.next != null) tmp.next = cur.next;
        }
        return newHead;
    }
}
```
## 总结
链表类问题，最重要的还是理清思路
