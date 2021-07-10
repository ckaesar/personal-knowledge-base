#### 删除排序链表中的重复元素

> 题目描述：存在一个按升序排列的链表，给你这个链表的头节点 head ，请你删除所有重复的元素，使每个元素 只出现一次 。
>
> 返回同样按升序排列的结果链表。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：链表遍历

> - 首先，如果head为null或者head只有一个结点，直接返回head；
> - 否则，从第二个结点开始遍历，记录当前结点为cur，当前的不重复的值为curVal，如果下一个结点的值等于curVal，则跳过这个结点，继续遍历下一个结点next，如果下一个结点的值不等有curVal，则更新curVal的值为下一个结点的值，且cur的下一个节点设置为next，知道遍历完成为为止，最后返回head。

```java
public class LeetCode_083 {
    public static ListNode deleteDuplicates(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode next = head.next, cur = head;
        int curVal = head.val;
        while (next != null) {
            if (next.val == curVal) {
                next = next.next;
                cur.next = null;
            } else {
                cur.next = next;
                cur = cur.next;
                curVal = next.val;
                next = next.next;
            }
        }
        return head;
    }

    public static void main(String[] args) {
        ListNode root = new ListNode(1);
        root.next = new ListNode(1);
        root.next.next = new ListNode(2);
        root.next.next.next = new ListNode(3);
        root.next.next.next.next = new ListNode(3);
        System.out.println("=====处理前=====");
        ListNode temp = root;
        while (temp != null) {
            System.out.print(temp.val + " ");
            temp = temp.next;
        }
        System.out.println();

        deleteDuplicates(root);
        System.out.println("=====处理后=====");
        while (root != null) {
            System.out.print(root.val + " ");
            root = root.next;
        }
    }
}
```

> 【每日寄语】 *但愿这漫长渺小人生，不负你每个光辉时分。* 

