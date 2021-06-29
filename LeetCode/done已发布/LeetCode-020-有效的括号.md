#### 有效的括号

> 题目描述：给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
>
> 有效字符串需满足：
>
> 左括号必须用相同类型的右括号闭合。
> 左括号必须以正确的顺序闭合。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/valid-parentheses/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：利用栈

> 初始化一个左括号栈**leftParentheses**，遍历字符串**s**的每个字符，当遇到左括号时，将当前字符**入栈**，当遇到右括号时，判断**leftParentheses**栈顶的字符是否是当前字符对应的左括号，如果不是，返回无效；否则**出栈**。遍历完成后，判断**leftParentheses是否为空**，如果不为空，说明左括号没有对应的右括号，返回无效；否则，有效。

```java
import java.util.Stack;

public class Solution {
    public static boolean isValid(String s) {
        if (s == null || s.length() == 0) {
            return true;
        }
        Stack<Character> leftParentheses = new Stack<>();
        for (char parentheses : s.toCharArray()) {
            if (parentheses == '(' || parentheses == '{' || parentheses == '[') {
                leftParentheses.push(parentheses);
            } else if (parentheses == ')') {
                if (leftParentheses.size() > 0 && leftParentheses.peek() == '(') {
                    leftParentheses.pop();
                } else {
                    return false;
                }
            } else if (parentheses == ']') {
                if (leftParentheses.size() > 0 && leftParentheses.peek() == '[') {
                    leftParentheses.pop();
                } else {
                    return false;
                }
            } else if (parentheses == '}') {
                if (leftParentheses.size() > 0 && leftParentheses.peek() == '{') {
                    leftParentheses.pop();
                } else {
                    return false;
                }
            }
        }
        if (leftParentheses.size() != 0) {
            return false;
        }
        return true;
    }

    public static void main(String[] args) {
        System.out.println(isValid("()[]{}"));
    }
}
```

【每日寄语】*每个睡醒后的早晨都是一件礼物，把每个开心后的微笑当成一个习惯，美好的一天从现在开始。* 
