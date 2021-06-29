#### 合并K个升序链表

> 题目描述：给你一个链表数组，每个链表都已经按升序排列。
>
> 请你将所有链表合并到一个升序链表中，返回合并后的链表。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/merge-k-sorted-lists/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：链表遍历

> - 首先，如果**lists**为null或者为空，直接返回null；
> - 然后，循环遍历数组中的链表，记录每一次遍历过程中的最小值**min**和相应的数组索引**minIndex**，将**min**放到结果**result**中，同时将数组索引为**minIndex**的链表往后移一位，遍历中止的条件就是当数组中所有的链表都为空时循环结束。  遍历结束后，返回结果**result**。

```java
public class LeetCode_023 {
    public static ListNode mergeKLists(ListNode[] lists) {
        if (lists == null || lists.length == 0) {
            return null;
        }

        int count = 0;
        ListNode result = new ListNode(-1);
        ListNode next = result;
        do {
            count = 0;
            int min = Integer.MAX_VALUE, minIndex = -1;
            for (int i = 0; i < lists.length; i++) {
                if (lists[i] != null) {
                    count++;
                    if (min > lists[i].val) {
                        min = lists[i].val;
                        minIndex = i;
                    }
                }
            }
            if (count > 0) {
                next.next = new ListNode(min);
                lists[minIndex] = lists[minIndex].next;
                next = next.next;
            }
        } while (count > 0);
        return result.next;
    }

    public static void main(String[] args) {
        ListNode l1 = new ListNode(1);
        l1.next = new ListNode(4);
        l1.next.next = new ListNode(5);

        ListNode l2 = new ListNode(1);
        l2.next = new ListNode(3);
        l2.next.next = new ListNode(4);

        ListNode l3 = new ListNode(2);
        l3.next = new ListNode(6);

        ListNode result = mergeKLists(new ListNode[]{l1, l2, l3});
        while (result != null) {
            System.out.print(result.val + " ");
            result = result.next;
        }
    }
}
```

> 【每日寄语】 *当所有事情看起来都像在跟你作对时，请记得飞机也是逆风起飞的，而不是顺风而起。* 

