#### 删除链表的倒数第 N 个结点

> 题目描述：给你一个链表，删除链表的倒数第 `n` 个结点，并且返回链表的头结点。
>
> **进阶：**你能尝试使用一趟扫描实现吗？
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：利用栈

> 首先遍历一遍链表，将结点的值放进栈**temp**里，然后遍历**temp**，过滤掉第**n**个结点，剩下的重新组装成链表**result**，返回**result**。
>
> 备注：进阶的做法可以采用**双指针法**，待优化。

```java
import java.util.Stack;

public class Solution {
    /**
     * 方法一：利用栈
     * @param head
     * @param n
     * @return
     */
    public static ListNode removeNthFromEnd(ListNode head, int n) {
        if (head == null) {
            return null;
        }
        Stack<Integer> temp = new Stack<>();
        while (head != null) {
            temp.push(head.val);
            head = head.next;
        }
        Stack<Integer> result = new Stack<>();
        int count = 1;
        boolean findN = false;
        while (!temp.isEmpty()) {
            if (count == n) {
                temp.pop();
                findN = true;
                count++;
                continue;
            }
            result.push(temp.pop());
            count++;
        }
        if (!findN) {
            return null;
        }
        ListNode resultNode = new ListNode(-1);
        ListNode next = resultNode;
        while (!result.isEmpty()) {
            next.next = new ListNode(result.pop());
            next = next.next;
        }
        return resultNode.next;
    }

    public static void main(String[] args) {
        ListNode root = new ListNode(1);
        root.next = new ListNode(2);
        root.next.next = new ListNode(3);
        root.next.next.next = new ListNode(4);
        root.next.next.next.next = new ListNode(5);
        root = removeNthFromEnd(root, 2);
        while (root != null) {
            System.out.print(root.val + "->");
            root = root.next;
        }
    }
}

class ListNode {
    int val;
    ListNode next;

    ListNode() {
    }

    ListNode(int val) {
        this.val = val;
    }

    ListNode(int val, ListNode next) {
        this.val = val;
        this.next = next;
    }
}
```

【每日寄语】*你今天的努力，是幸运的伏笔，当下的付出，是明日的花开。* 

