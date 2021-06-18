#### 两两交换链表中的节点

> 题目描述：给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。
>
> 你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/swap-nodes-in-pairs/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：双指针法

> - 首先，如果head为空或者head没有后继节点，直接返回head；
>
> - 然后用2个指针first和second分别指向第一个和第二个节点，new一个pre节点指向first，操作过程如下：
>
>   - first的next指向second的next；
>
>   - second的next指向first；
>
>   - pre的next指向second；
>
>   - 前面几步就是把first和second的位置交换；
>
>   - 然后pre指向first；
>
>   - first指向first的next；
>
>   - 然后进行下一次遍历，条件是first不为空且first的next不为空，直到这个条件不成立，则遍历结束。
>
>   - 返回结果。
>
>     

```java
public class LeetCode_024 {
    public static ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode newHead = head.next;
        ListNode pre = new ListNode(-1), first = head, second;
        pre.next = head;
        while (first != null && first.next != null) {
            second = first.next;

            first.next = second.next;
            second.next = first;
            pre.next = second;

            pre = first;
            first = first.next;
        }

        return newHead;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        ListNode result = swapPairs(head);
        while (result != null) {
            System.out.print(result.val + " ");
            result = result.next;
        }
    }
}
```

> 【每日寄语】 *宇宙山河浪漫，生活点滴温暖，都值得你我前进。* 

