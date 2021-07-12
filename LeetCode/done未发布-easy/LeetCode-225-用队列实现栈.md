#### 用队列实现栈

> 题目描述：请你仅使用两个队列实现一个后入先出（LIFO）的栈，并支持普通队列的全部四种操作（push、top、pop 和 empty）。
>
> 实现 MyStack 类：
>
> - void push(int x) 将元素 x 压入栈顶。
> - int pop() 移除并返回栈顶元素。
> - int top() 返回栈顶元素。
> - boolean empty() 如果栈是空的，返回 true ；否则，返回 false 。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/implement-stack-using-queues/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：双队列实现栈

> 使用2个队列firstQueue和secondQueue存储数据，具体方法说明如下：
>
> - `push(int x)`：如果firstQueue为空，则将x存到secondQueue中，否则存到firstQueue中；
> - `pop()`：如果firstQueue为空，则将secondQueue中的数据都取出然后依次存入firstQueue中只留一个作为栈顶元素取出并返回；否则，将firstQueue中的数据都取出然后依次存入secondQueue中只留一个作为栈顶元素取出并返回；
> - `top()`：逻辑通`pop()`方法类似；
> - `empty()`：如果firstQueue和secondQueue都为空，返回true；否则，返回false。

```java
import java.util.LinkedList;
import java.util.Queue;

public class LeetCode_225 {
    public static void main(String[] args) {
        MyStack myStack = new MyStack();
        myStack.push(1);
        myStack.push(2);
        myStack.push(3);
        System.out.println(myStack.top()); // 返回 2
        System.out.println(myStack.pop()); // 返回 2
        System.out.println(myStack.empty()); // 返回 False
    }
}

class MyStack {
    private Queue<Integer> firstQueue;
    private Queue<Integer> secondQueue;

    /**
     * Initialize your data structure here.
     */
    public MyStack() {
        firstQueue = new LinkedList<>();
        secondQueue = new LinkedList<>();
    }

    /**
     * Push element x onto stack.
     */
    public void push(int x) {
        if (firstQueue == null) {
            secondQueue.add(x);
        } else {
            firstQueue.add(x);
        }
    }

    /**
     * Removes the element on top of the stack and returns that element.
     */
    public int pop() {
        if (this.empty()) {
            throw new RuntimeException("empty stack.");
        }
        if (firstQueue.isEmpty()) {
            int size = secondQueue.size();
            for (int i = 1; i < size; i++) {
                firstQueue.add(secondQueue.poll());
            }
            return secondQueue.poll();
        } else {
            int size = firstQueue.size();
            for (int i = 1; i < size; i++) {
                secondQueue.add(firstQueue.poll());
            }
            return firstQueue.poll();
        }
    }

    /**
     * Get the top element.
     */
    public int top() {
        if (this.empty()) {
            throw new RuntimeException("empty stack.");
        }
        int result = -1;
        if (firstQueue.isEmpty()) {
            int size = secondQueue.size();
            for (int i = 1; i < size; i++) {
                firstQueue.add(secondQueue.poll());
            }
            result = secondQueue.peek();
            firstQueue.add(secondQueue.poll());
        } else {
            int size = firstQueue.size();
            for (int i = 1; i < size; i++) {
                secondQueue.add(firstQueue.poll());
            }
            result = firstQueue.peek();
            secondQueue.add(firstQueue.poll());
        }
        return result;
    }

    /**
     * Returns whether the stack is empty.
     */
    public boolean empty() {
        return firstQueue.isEmpty() && secondQueue.isEmpty();
    }
}
```

> 【每日寄语】 *哪怕生活不宠你，也要好好善待自己。这一生，风雨兼程，就是为了遇见最好的自己。* 

