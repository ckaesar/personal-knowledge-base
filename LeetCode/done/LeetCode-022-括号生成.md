#### 括号生成

> 题目描述：数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。
>
> 示例说明请见LeetCode官网。
>
> 来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/generate-parentheses/
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。

###### 解法一：暴力破解法

> 描述

###### 解法二：回溯法

> 描述

```java
import java.util.ArrayList;
import java.util.List;

public class LeetCode_022 {
    /**
     * 暴力破解法
     *
     * @param n
     * @return
     */
    public static List<String> generateParenthesis(int n) {
        List<String> allPossibleResults = new ArrayList<>();
        generateAllPossibleResults(new char[2 * n], 0, allPossibleResults);
        return allPossibleResults;
    }

    public static void generateAllPossibleResults(char[] current, int pos, List<String> result) {
        if (pos == current.length) {
            if (valid(current)) {
                result.add(new String(current));
            }
        } else {
            current[pos] = '(';
            generateAllPossibleResults(current, pos + 1, result);
            current[pos] = ')';
            generateAllPossibleResults(current, pos + 1, result);
        }
    }

    public static boolean valid(char[] current) {
        int balance = 0;
        for (char c : current) {
            if (c == '(') {
                ++balance;
            } else {
                --balance;
            }
            if (balance < 0) {
                return false;
            }
        }
        return balance == 0;
    }

    static List<String> res = new ArrayList<>();

    /**
     * 方法二：回溯法
     *
     * @param n
     * @return
     */
    public static List<String> generateParenthesis2(int n) {
        if (n <= 0) {
            return res;
        }
        getParenthesis("", n, n);
        return res;
    }

    private static void getParenthesis(String str, int left, int right) {
        if (left == 0 && right == 0) {
            res.add(str);
            return;
        }
        if (left == right) {
            //剩余左右括号数相等，下一个只能用左括号
            getParenthesis(str + "(", left - 1, right);
        } else if (left < right) {
            //剩余左括号小于右括号，下一个可以用左括号也可以用右括号
            if (left > 0) {
                getParenthesis(str + "(", left - 1, right);
            }
            getParenthesis(str + ")", left, right - 1);
        }
    }

    public static void main(String[] args) {
        List<String> strings = generateParenthesis(4);
        for (String string : strings) {
            System.out.println(string);
        }
        System.out.println("=====================");
        List<String> strings1 = generateParenthesis2(4);
        for (String s : strings1) {
            System.out.println(s);
        }
    }
}
```

> 【每日寄语】 *一万个美丽的未来，抵不上一个温暖的现在。* 

