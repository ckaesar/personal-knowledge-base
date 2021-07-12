#### 最小栈

> 题目描述：设计一个支持 push ，pop ，top 操作，并能在常数时间内检索到最小元素的栈。
>
> - push(x) —— 将元素 x 推入栈中。
> - pop() —— 删除栈顶的元素。
> - top() —— 获取栈顶元素。
> - getMin() —— 检索栈中的最小元素。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/min-stack/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：双栈

> 利用2个栈，一个栈data存储数据，一个栈minVal存储最小值，具体方法逻辑：
>
> - `push()`：将val值放到data的栈顶，判断val值是否小于等于minVal的栈顶元素，如果是，则将val值也放到minVal的栈顶；
> - `pop()`：将data的栈顶元素取出，判断如果取出的元素等于minVal的栈顶元素，则将minVal的栈顶元素也取出；
> - `top()`：查看data的栈顶元素；
> - `getMin()`：查看minVal的栈顶元素。

```java
import java.util.Stack;

public class LeetCode_155 {
    public static void main(String[] args) {
        MinStack minStack = new MinStack();
        minStack.push(-2);
        minStack.push(0);
        minStack.push(-3);
        System.out.println(minStack.getMin());   // 返回 -3.
        minStack.pop();
        System.out.println(minStack.top());      // 返回 0.
        System.out.println(minStack.getMin());   // 返回 -2.
    }
}

class MinStack {
    private Stack<Integer> data;
    private Stack<Integer> minVal;

    /**
     * initialize your data structure here.
     */
    public MinStack() {
        data = new Stack<>();
        minVal = new Stack<>();
    }

    public void push(int val) {
        data.push(val);
        if (minVal.isEmpty()) {
            minVal.push(val);
        } else if (val <= minVal.peek()) {
            minVal.push(val);
        }
    }

    public void pop() {
        if (data.isEmpty()) {
            throw new RuntimeException("stack is empty.");
        }
        int popVal = data.pop();
        if (popVal == minVal.peek()) {
            minVal.pop();
        }
    }

    public int top() {
        return data.peek();
    }

    public int getMin() {
        if (minVal.isEmpty()) {
            throw new RuntimeException("stack is empty.");
        }
        return minVal.peek();
    }
}
```

> 【每日寄语】 *不去追逐，永远不会拥有。不往前走，永远原地停留。知道自己目的地的人，才是旅行得最远的人。* 

