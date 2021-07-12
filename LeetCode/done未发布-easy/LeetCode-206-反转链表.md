#### 反转链表

> 题目描述：给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/reverse-linked-list/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：迭代

> 首先，如果head为null或者head只有一个结点，直接返回head；
>
> 否则，声明2个参数first和second分别是head的第一个和第二个结点，然后遍历链表：
>
> - 声明temp为second的next结点；
> - 将second的next指向first（反转）；
> - 将first指向second，second指向temp（同时后移，处理下一个结点）；
> - 当second为null时说明遍历到链表的终点了，此时终止遍历，first即为反转后新的头结点。

```java
public class LeetCode_206 {
    public static ListNode reverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode first = head, second = head.next;
        first.next = null;
        while (first != null && second != null) {
            ListNode temp = second.next;
            second.next = first;
            first = second;
            second = temp;
        }
        return first;
    }

    public static void main(String[] args) {
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        ListNode result = reverseList(head);
        while (result != null) {
            System.out.print(result.val + " ");
            result = result.next;
        }
    }
}
```

> 【每日寄语】 *总有一天，你会站在最亮的地方，活成自己曾经渴望的模样。* 

