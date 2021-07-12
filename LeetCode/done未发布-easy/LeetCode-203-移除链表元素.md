#### 移除链表元素

> 题目描述：给你一个链表的头节点 head 和一个整数 val ，请你删除链表中所有满足 Node.val == val 的节点，并返回 新的头节点 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/remove-linked-list-elements/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：链表遍历

> 首先，初始化一个结点firstNode指向head结点，cur指向head结点，last指向firstNode结点，然后开始遍历：
>
> - 首先cur不能为空；
> - 如果cur结点的值等于目标值val，则将last的next指向cur的next，并且cur赋值为cur的next；
> - 如果cur结点的值不等于目标值val，则将last和cur结点往后移一位。
>
> 遍历结束后，返回firstNode的next结点即为处理后的链表。

```java
public class LeetCode_203 {
    public static ListNode removeElements(ListNode head, int val) {
        ListNode firstNode = new ListNode(-1);
        firstNode.next = head;
        ListNode cur = firstNode.next;
        ListNode last = firstNode;
        while (cur != null) {
            if (cur.val == val) {
                last.next = cur.next;
                cur = last.next;
            } else {
                last = cur;
                cur = cur.next;
            }
        }
        return firstNode.next;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(6);
        head.next.next.next = new ListNode(3);
        head.next.next.next.next = new ListNode(6);

        removeElements(head, 6);
        while (head != null) {
            System.out.print(head.val + " ");
            head = head.next;
        }
    }
}
```

> 【每日寄语】 *在这个并非尽善尽美的世界上，勤奋会得到报偿，而游手好闲则要受到惩罚。* 

